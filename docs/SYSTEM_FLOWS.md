# Taqdimah : System Flows (Complete)

**Version:** 1.0  
**Parent:** [PRD-TECHNICAL.md](./PRD-TECHNICAL.md)

---

## Flow Index

| # | Flow | Actor | Phase |
|---|------|-------|-------|
| 1 | Consumer search to lead | Consumer | P0 |
| 2 | Vendor onboarding to live | Vendor | P0 |
| 3 | Verification approval | Admin | P0 |
| 4 | Review lifecycle | Consumer + Vendor | P0 |
| 5 | Featured listing purchase | Vendor + Admin | P1 |
| 6 | Ecosystem marketing loop | Platform | P0 |
| 7 | Institution onboarding | Institution | P1 |
| 8 | AI intent bundle | Consumer | P2 |
| 9 | Payment escrow | Consumer + Vendor | P2 |
| 10 | Partner API lead | Partner | P3 |

---

## Flow 1: Consumer Search → Lead → Review

```mermaid
sequenceDiagram
    autonumber
    participant C as Consumer
    participant FE as Web App
    participant Search as SearchService
    participant DB as PostgreSQL
    participant Lead as LeadService
    participant Notify as NotificationService
    participant V as Vendor

    C->>FE: Enter "halal catering uttara 200 guests"
    FE->>Search: GET /api/search?q=...
    Search->>Search: parseIntent()
    Search->>DB: FTS + rank verified vendors
    DB-->>Search: 12 results
    Search-->>FE: Results + intent
    FE-->>C: Display ranked cards

    C->>FE: Open profile "Barakah Catering"
    FE->>DB: GET vendor + increment views
    FE-->>C: Profile page

    C->>FE: Click "Request Quote"
    alt Not logged in
        FE->>C: OTP login modal
        C->>FE: Verify OTP
    end
    C->>FE: Submit lead form
    FE->>Lead: POST /api/leads
    Lead->>Lead: checkQuota(vendor)
    Lead->>DB: INSERT lead status=sent
    Lead->>Notify: enqueue lead_new
    Notify->>V: Email + SMS
    Lead-->>FE: 201 Created
    FE-->>C: "Request sent"

    V->>FE: Open vendor dashboard
    V->>FE: Respond to lead
    FE->>DB: PATCH lead status=responded
    Notify->>C: "Vendor responded"

    C->>V: Complete job (off-platform Phase 1)
    C->>FE: Mark lead closed
    Note over FE: Wait 7 days
    Notify->>C: Review prompt
    C->>FE: Submit 5★ review
    FE->>DB: INSERT review
    FE->>DB: Recalculate trust_score
    FE->>DB: Refresh search_index
```

---

## Flow 2: Vendor Onboarding → Live Profile

```mermaid
flowchart TD
    A[Vendor sees ecosystem demand post] --> B[Visit /register/vendor]
    B --> C[Phone OTP signup]
    C --> D[Create draft VendorProfile]
    D --> E[Fill business info 60%+ complete]
    E --> F[Select categories + service areas]
    F --> G[Upload logo + portfolio]
    G --> H[Submit L2 identity docs]
    H --> I[Submit L3 trade license]
    I --> J[Status: pending]
    J --> K{Admin review 48h}
    K -->|Approve| L[verification_status=verified]
    K -->|Reject| M[Email reason + resubmit]
    M --> E
    L --> N[Add to search_index]
    N --> O[Profile live at /v/slug]
    O --> P[First free lead within 14 days target]
```

---

## Flow 3: Admin Verification

```mermaid
sequenceDiagram
    participant M as Moderator
    participant Admin as Admin Panel
    participant DB as Database
    participant Outbox as event_outbox
    participant Vendor as Vendor

    M->>Admin: Open verification queue
    Admin->>DB: SELECT pending ORDER BY created_at
    M->>Admin: Open request + view docs
    M->>Admin: Approve L3
    Admin->>DB: UPDATE verification_requests
    Admin->>DB: UPDATE vendor verification_level=3, status=verified
    Admin->>DB: INSERT admin_audit_log
    Admin->>Outbox: vendor.verified event
    Outbox->>DB: REFRESH search_index
    Admin->>Vendor: Email approval
```

---

## Flow 4: Trust Score Recalculation

```mermaid
flowchart TD
    E[Trigger Event] --> T{Event type}
    T -->|review.created| R[Fetch all reviews]
    T -->|lead.responded| Resp[Calc response_rate]
    T -->|vendor.updated| Comp[Calc completeness]
    T -->|verification.approved| V[Update level score]
    R --> Bayes[Bayesian avg rating]
    Resp --> Merge[Merge weighted formula]
    Comp --> Merge
    V --> Merge
    Bayes --> Merge
    Merge --> Update[UPDATE vendor_profiles.trust_score]
    Update --> Cache[Invalidate search cache]
    Cache --> Done[Done]
```

---

## Flow 5: Featured Listing (P1)

```mermaid
sequenceDiagram
    participant V as Vendor
    participant FE as Dashboard
    participant Bill as BillingService
    participant Admin as Admin
    participant Search as SearchService

    V->>FE: Request featured slot
    FE->>Bill: Check plan + payment
    alt Manual payment Phase 1
        Bill-->>V: bKash/Nagad instructions
        V->>Admin: Payment proof
        Admin->>FE: Create featured_slot
    end
    FE->>Search: Invalidate featured cache
    Note over Search: Featured at positions 1,4,8
```

---

## Flow 6: Ecosystem Marketing Loop

```mermaid
flowchart TD
    subgraph DemandGen["Demand Generation"]
        P1[Post: Sylhet needs architect]
        P2[Post: Dhaka startup needs dev]
        P3[SEO: /dhaka/quran-teachers ranks]
    end

    subgraph SupplyGen["Supply Generation"]
        S1[Vendor sees post → signs up]
        S2[Competitor on Taqdimah → FOMO]
        S3[Mosque QR flyer]
    end

    subgraph Platform["Platform Value"]
        V1[Better search results]
        V2[Reviews build trust]
        V3[Success stories shared]
    end

    DemandGen --> Platform
    Platform --> SupplyGen
    SupplyGen --> Platform
    V3 --> DemandGen
```

---

## Flow 7: Zero Search Results Fallback

```mermaid
flowchart TD
    Q[Query executed] --> R{results_count = 0?}
    R -->|No| Show[Show results]
    R -->|Yes| B1[Broaden area filter]
    B1 --> R2{Found?}
    R2 -->|Yes| Show
    R2 -->|No| B2[Broaden to city-wide]
    B2 --> R3{Found?}
    R3 -->|Yes| Show
    R3 -->|No| B3[Suggest related categories]
    B3 --> CTA[CTA: Post open request]
    CTA --> Lead[Create broadcast lead P2]
```

---

## Flow 8: AI Intent Bundle (P2)

```mermaid
sequenceDiagram
    participant C as Consumer
    participant AI as AI Orchestrator
    participant Search as SearchService
    participant Lead as LeadService

    C->>AI: "I'm moving to Banani next Friday"
    AI->>AI: Extract life event + location + date
    AI->>Search: Multi-category bundle query
    Search-->>AI: Vendors per category
    AI-->>C: Bundle UI: Moving, Electrician, Cleaning
    C->>C: Select all or subset
    C->>Lead: Create multi lead_assignments
    Lead->>Lead: Notify each vendor
```

---

## Flow 9: Payment Escrow (P2)

```mermaid
stateDiagram-v2
    [*] --> quoted: Vendor sends quote
    quoted --> payment_pending: User accepts
    payment_pending --> escrow_held: SSLCommerz success
    escrow_held --> in_progress: Vendor starts job
    in_progress --> completed: Vendor marks done
    completed --> released: User confirms
    released --> [*]: Funds to vendor minus fee
    completed --> disputed: User disputes
    disputed --> refunded: Admin resolves refund
    disputed --> released: Admin resolves release
```

---

## Flow 10: Vendor Claim Pre-Seeded Profile

```mermaid
sequenceDiagram
    participant V as Vendor
    participant FE as App
    participant DB as Database

    Note over DB: Admin imported 100 vendors
    V->>FE: Finds own listing unclaimed
    V->>FE: Click "Claim this business"
    FE->>V: OTP to listed phone
    V->>FE: Verify OTP
    FE->>DB: Link user_id, claimed_from_seed=true
    FE->>V: Complete profile + submit verification
```

---

## User State Machines Summary

### Lead states

`sent` → `viewed` → `responded` → `closed`  
Branches: `expired`, `spam`, `disputed`

### Vendor verification states

`draft` → `pending` → `verified` | `rejected`  
Branches: `suspended`, `banned`

### Subscription states

`free` → `pro` → `business`  
Branches: `past_due`, `cancelled`

---

**Related:** [API_REFERENCE.md](./API_REFERENCE.md) · [TRUST_SYSTEM.md](./TRUST_SYSTEM.md)