# Taqdimah : Payments & Escrow (Phase 2 Design)

**Version:** 1.0  
**Phase:** P2 : implement after MVP lead loop proven  
**Parent:** [BUSINESS_PLAN.md](./BUSINESS_PLAN.md) · [PRD-TECHNICAL.md](./PRD-TECHNICAL.md) §16

---

## 1. Objectives

1. Enable **in-platform booking payment** with transparent fees
2. **Escrow** protects consumers and vendors
3. **Halal-aligned** : no interest; ju'ālah (commission) disclosed upfront
4. Bangladesh first: **SSLCommerz**; global: **Stripe**

---

## 2. Payment Flow

```mermaid
sequenceDiagram
    participant C as Consumer
    participant A as Taqdimah
    participant G as SSLCommerz
    participant V as Vendor

    C->>A: Accept vendor quote 10,000 BDT
    A->>C: Show total 10,500 BDT (fee disclosed)
    C->>G: Payment session
    G-->>A: Webhook payment success
    A->>A: Create escrow held
    V->>A: Mark job in progress
    V->>A: Mark completed
    C->>A: Confirm satisfaction
    A->>G: Settle 9,500 to vendor (95%)
    A->>A: Platform fee 1,000 (10%)
```

---

## 3. State Machine

```mermaid
stateDiagram-v2
    [*] --> quoted
    quoted --> payment_pending: user accepts
    payment_pending --> escrow_held: payment success
    payment_pending --> cancelled: timeout 24h
    escrow_held --> in_progress: vendor starts
    in_progress --> completed: vendor marks done
    completed --> released: user confirms
    completed --> disputed: user disputes within 72h
    disputed --> released: admin favors vendor
    disputed --> refunded: admin favors user
    released --> [*]
    refunded --> [*]
```

---

## 4. Fee Structure

| Category | Platform fee | Rationale |
|----------|--------------|-----------|
| Home services | 8% | Standard marketplace |
| Professional | 10% | Higher ticket |
| Islamic education | 5% | Community incentive |
| Catering / events | 10% | Coordination heavy |

**Display rule:** Fee shown before payment confirmation. Never hidden.

---

## 5. Data Model

```sql
CREATE TABLE payment_transactions (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  lead_id UUID REFERENCES leads(id),
  user_id UUID REFERENCES profiles(id),
  vendor_id UUID REFERENCES vendor_profiles(id),
  amount DECIMAL(12,2) NOT NULL,
  platform_fee DECIMAL(12,2) NOT NULL,
  vendor_payout DECIMAL(12,2) NOT NULL,
  currency TEXT DEFAULT 'BDT',
  status TEXT CHECK (status IN (
    'pending','escrow_held','released','refunded','disputed','failed'
  )),
  gateway TEXT DEFAULT 'sslcommerz',
  gateway_tran_id TEXT UNIQUE,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  released_at TIMESTAMPTZ
);
```

---

## 6. Islamic Finance Integration (Referral : not lending)

Taqdimah does **not** hold loans. Referral flow:

```mermaid
flowchart LR
    User[User needs halal financing] --> Page[Islamic finance category]
    Page --> Partner[Partner bank / fintech]
    Partner --> Apply[User applies on partner site]
    Partner --> Webhook[Referral confirmation webhook]
    Webhook --> Taqdimah[Taqdimah referral fee]
```

**Shariah board approval required** before any partner listed.

---

## 7. Waqf & Donation (Phase 3)

- Donations flow to NGO payment account directly
- Optional platform tip: user-visible, max 5%
- Full receipt from NGO, not Taqdimah

---

## 8. Compliance

- PCI: delegated to SSLCommerz/Stripe
- KYC: vendor bank account verification before payout
- Tax: VAT invoice generation Bangladesh NBR rules
- Refund policy: published, 72h dispute window

---

**Related:** [BUSINESS_PLAN.md](./BUSINESS_PLAN.md) · [EVENTS.md](./EVENTS.md)