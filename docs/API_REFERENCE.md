# Taqdimah : API Reference

**Version:** 1.0  
**Base URL:** `https://Taqdimah.app/api` (production)  
**Auth:** httpOnly session cookie or `Authorization: Bearer <jwt>`  
**Content-Type:** `application/json`

---

## Conventions

### Response envelope (success)

```json
{
  "data": { },
  "meta": {
    "request_id": "req_abc123",
    "timestamp": "2026-07-03T12:00:00Z"
  }
}
```

### Response envelope (error)

```json
{
  "error": {
    "code": "QUOTA_EXCEEDED",
    "message": "Free plan lead limit reached for this month",
    "details": { "limit": 10, "used": 10 },
    "request_id": "req_abc123"
  }
}
```

### Pagination

```json
{
  "data": [],
  "meta": {
    "page": 1,
    "limit": 20,
    "total": 150,
    "has_more": true,
    "next_cursor": "eyJpZCI6..."
  }
}
```

---

## Authentication

### POST /api/auth/otp/send

Send OTP to Bangladesh phone number.

**Body:**
```json
{ "phone": "+8801712345678" }
```

**Response 200:**
```json
{ "data": { "success": true, "retry_after": null } }
```

**Errors:** `AUTH_RATE_LIMITED` (429), `VALIDATION_ERROR` (400)

---

### POST /api/auth/otp/verify

**Body:**
```json
{ "phone": "+8801712345678", "token": "123456" }
```

**Response 200:** Sets session cookie + returns user profile.

---

### POST /api/auth/google

**Body:**
```json
{ "code": "oauth_authorization_code" }
```

---

### POST /api/auth/logout

Clears session. **Auth required.**

---

### GET /api/auth/session

**Response:**
```json
{
  "data": {
    "user": {
      "id": "uuid",
      "role": "vendor",
      "full_name": "Karim Ahmed",
      "locale": "bn",
      "vendor_id": "uuid"
    }
  }
}
```

---

## Search & Discovery

### GET /api/search

**Query parameters:**

| Param | Type | Required | Description |
|-------|------|----------|-------------|
| q | string | Yes | Natural language query |
| city | string | No | City slug e.g. `dhaka` |
| category | string | No | Force category slug |
| page | int | No | Default 1 |
| limit | int | No | Default 20, max 50 |
| hide_sponsored | bool | No | Default false |

**Response 200:**
```json
{
  "data": {
    "query": "AC repair mirpur",
    "intent": {
      "category_slug": "ac-repair",
      "city": "dhaka",
      "area": "mirpur",
      "language": "mixed",
      "confidence": 0.92
    },
    "results": [
      {
        "id": "uuid",
        "slug": "cool-air-dhaka",
        "business_name": "Cool Air Services",
        "tagline": "24/7 AC repair Mirpur",
        "trust_score": 4.6,
        "verification_level": 3,
        "avg_rating": 4.5,
        "review_count": 28,
        "halal_badge": false,
        "is_featured": true,
        "placement_type": "featured",
        "primary_category": {
          "slug": "ac-repair",
          "name": "AC Repair"
        },
        "service_areas": ["mirpur", "pallabi"]
      }
    ]
  },
  "meta": { "total": 12, "page": 1, "limit": 20, "has_more": false }
}
```

---

### GET /api/categories

Returns category tree.

**Query:** `parent_slug`, `locale` (en|bn)

---

### GET /api/categories/[slug]

Single category with SEO metadata + top vendors preview.

---

### GET /api/cities

List active cities with areas.

---

### GET /api/autocomplete

**Query:** `q` (min 2 chars)

**Response:** `{ "suggestions": ["AC repair", "Architects in Dhaka", ...] }`

---

## Vendors (Public)

### GET /api/vendors/[slug]

Full public vendor profile.

**Response includes:**
- Profile fields
- Portfolio
- Reviews (paginated)
- Categories
- Trust breakdown summary (not internal weights)
- `can_request_lead: true`

**Side effect:** Increments `profile_views` async.

---

## Leads

### POST /api/leads

**Auth:** required (user or vendor)

**Body:**
```json
{
  "vendor_id": "uuid",
  "category_id": "uuid",
  "description": "Need AC gas refill for 2 split units",
  "location_city": "dhaka",
  "location_area": "mirpur",
  "budget_min": 1500,
  "budget_max": 3000,
  "urgency": "medium",
  "contact_phone": "+8801712345678",
  "contact_method": "whatsapp"
}
```

**Response 201:**
```json
{
  "data": {
    "id": "uuid",
    "status": "sent",
    "vendor_id": "uuid",
    "created_at": "2026-07-03T12:00:00Z"
  }
}
```

**Errors:**
- `QUOTA_EXCEEDED` (402) : vendor free plan full
- `RATE_LIMITED` (429) : user 5/day exceeded
- `VENDOR_NOT_ELIGIBLE` (400) : vendor not verified

---

### GET /api/leads

**Auth:** user sees own leads; vendor sees received leads.

**Query:** `status`, `page`, `limit`

---

### GET /api/leads/[id]

**Auth:** lead participant only

---

### PATCH /api/leads/[id]

**Auth:** vendor or user depending on action

**Vendor body:**
```json
{ "status": "responded", "vendor_response": "We can visit tomorrow 10am. Cost approx 2500 BDT." }
```

**User body:**
```json
{ "status": "closed" }
```

---

## Reviews

### POST /api/reviews

**Auth:** user with closed lead

**Body:**
```json
{
  "lead_id": "uuid",
  "rating": 5,
  "comment": "Fast and professional service"
}
```

---

### GET /api/vendors/[slug]/reviews

**Public.** Paginated.

---

### POST /api/reviews/[id]/reply

**Auth:** vendor owner

**Body:** `{ "vendor_reply": "Thank you for your kind words!" }`

---

## Vendor Dashboard

### GET /api/vendor/dashboard

**Auth:** vendor

**Response:**
```json
{
  "data": {
    "profile_views_week": 45,
    "leads_week": 8,
    "trust_score": 4.3,
    "response_rate": 87.5,
    "plan": "free",
    "leads_remaining": 2,
    "profile_completeness": 85
  }
}
```

---

### PATCH /api/vendor/profile

**Auth:** vendor

**Body:** Partial vendor profile fields.

---

### POST /api/vendor/verification

**Auth:** vendor

**Body:**
```json
{
  "level": 3,
  "document_type": "trade_license",
  "document_urls": ["https://storage.../doc1.pdf"]
}
```

---

### GET /api/vendor/leads

Alias of GET /api/leads with vendor scope + filters.

---

## Billing

### GET /api/vendor/billing

**Auth:** vendor

**Response:** plan, quota, usage, invoices summary.

---

### POST /api/vendor/billing/upgrade

**Auth:** vendor

**Body:** `{ "plan": "pro" }`

Phase 1: returns payment instructions. Phase 2: SSLCommerz session.

---

## Institutions (P1)

### GET /api/institutions/[slug]

Public institution profile.

---

### POST /api/institutions

**Auth:** institution admin (onboarding flow)

---

## Admin

### GET /api/admin/verification-queue

**Auth:** moderator, admin

**Query:** `status=pending`, `assigned_to`

---

### PATCH /api/admin/verification/[id]

**Body:**
```json
{ "decision": "approved", "notes": "Trade license valid until 2027" }
```

---

### POST /api/admin/vendors/import

**Content-Type:** `multipart/form-data` CSV

**Columns:** business_name, phone, category_slug, city, description

---

### POST /api/admin/featured-slots

**Body:**
```json
{
  "vendor_id": "uuid",
  "category_id": "uuid",
  "city": "dhaka",
  "slot_type": "featured",
  "starts_at": "2026-08-01T00:00:00Z",
  "ends_at": "2026-08-31T23:59:59Z"
}
```

---

### GET /api/admin/metrics

**Response:** MQL, MAU, vendors, searches, revenue snapshot.

---

## Reports

### POST /api/reports

**Auth:** optional (logged in preferred)

**Body:**
```json
{
  "entity_type": "vendor",
  "entity_id": "uuid",
  "reason": "fake_listing"
}
```

---

## Webhooks (Phase 2)

### POST /api/webhooks/sslcommerz

Payment confirmation. Idempotent by `tran_id`.

### POST /api/webhooks/whatsapp

Inbound message routing to lead threads.

---

## Rate Limits

| Endpoint | Anonymous | Authenticated |
|----------|-----------|---------------|
| /api/search | 30/min | 60/min |
| /api/leads POST | : | 5/day |
| /api/auth/otp/send | 3/hour/phone | : |

**Headers returned:**
```
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 45
X-RateLimit-Reset: 1710000060
```

---

## Webhook Events (Outbound : Phase 3)

Partners subscribe to:

| Event | Payload |
|-------|---------|
| `lead.created` | Lead object |
| `vendor.verified` | Vendor object |
| `review.created` | Review object |

```
POST partner_url
X-Taqdimah-Signature: sha256=...
{ "type": "lead.created", "data": { ... } }
```

---

**Related:** [TECHNICAL_DESIGN.md](./TECHNICAL_DESIGN.md) · [SYSTEM_FLOWS.md](./SYSTEM_FLOWS.md)