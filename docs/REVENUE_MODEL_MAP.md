# Taqdimah : Business & Revenue Model Maps (Visual)

> **All ways Taqdimah can earn money** : mapped visually.  
> Companion to [BUSINESS_PLAN.md](./BUSINESS_PLAN.md) · [GUIDELINE_MAP.md](./GUIDELINE_MAP.md) Diagram 6

**Principle:** Transparent fees. No riba. No hidden ads. Serve the Ummah : don't extract from it.

---

## Map 1 : Business Model at a Glance (Who Pays for What)

```mermaid
flowchart TB
    subgraph CUSTOMERS["Who uses Taqdimah FREE"]
        U1[Muslim consumers<br/>search + request quotes]
        U2[Mosque / NGO visitors<br/>find institutions]
    end

    subgraph PAYERS["Who PAYS Taqdimah"]
        direction TB
        P1[Vendors / SMEs<br/>subscriptions + leads]
        P2[Professionals<br/>featured placement]
        P3[Restaurants / caterers<br/>halal badge + leads]
        P4[Institutions<br/>premium campaign tools]
        P5[Islamic finance partners<br/>referral fees]
        P6[Enterprise partners<br/>API access]
        P7[Brands<br/>sponsored search]
    end

    subgraph PLATFORM["What Taqdimah provides"]
        PL1["Discovery : find vendors"]
        PL2["Trust : verification + reviews"]
        PL3["Leads : customer introductions"]
        PL4["Tools : vendor dashboard"]
        PL5["Reach : SEO + ecosystem marketing"]
    end

    CUSTOMERS --> PLATFORM
    PAYERS -->|money| PLATFORM
    PLATFORM -->|customers| PAYERS

    style PAYERS fill:#fef9e7,stroke:#f39c12
    style CUSTOMERS fill:#eafaf1,stroke:#27ae60
    style PLATFORM fill:#e8f4f8,stroke:#2980b9
```

**Key insight:** Consumers never pay for search. Vendors and partners pay for **access to trusted demand**.

---

## Map 2 : All 12 Revenue Streams (Complete List)

```mermaid
mindmap
  root((Taqdimah Revenue))
    Phase 1 MVP
      R1 Vendor SaaS Free tier
      R2 Vendor SaaS Pro 999 BDT
      R3 Vendor SaaS Business 2499 BDT
      R4 Featured listings
      R5 Pay per lead
      R6 Sponsored search CPC
    Phase 2 Transactions
      R7 Booking fee 5 to 12 percent
      R8 Payment escrow margin
      R9 Premium institution pages
    Phase 3 Ecosystem
      R10 Islamic finance referrals
      R11 Waqf charity platform fee
      R12 Enterprise API licensing
      R13 Market insights reports
      R14 Vendor AI copilot add-on
```

---

## Map 3 : Revenue Stream Detail Matrix

```mermaid
flowchart LR
    subgraph S1["R1–R3: SaaS Subscriptions"]
        direction TB
        A1["Free: 0 BDT<br/>10 leads/mo"]
        A2["Pro: 999 BDT/mo<br/>unlimited leads + analytics"]
        A3["Business: 2499 BDT/mo<br/>featured rotation + API read"]
    end

    subgraph S2["R4–R6: Visibility"]
        direction TB
        B1["Featured slot<br/>1500–5000 BDT/mo"]
        B2["City homepage banner<br/>10000+ BDT/mo"]
        B3["Sponsored search<br/>15–30 BDT per click"]
    end

    subgraph S3["R5 + R7–R8: Transaction Layer"]
        direction TB
        C1["Pay per lead<br/>50–500 BDT"]
        C2["Booking commission<br/>5–12 percent"]
        C3["Escrow processing<br/>included in commission"]
    end

    subgraph S4["R10–R14: Ecosystem"]
        direction TB
        D1["Islamic bank referral<br/>fixed fee per account"]
        D2["Takaful referral<br/>per policy"]
        D3["Waqf campaign fee<br/>capped 2–5 percent"]
        D4["Enterprise API<br/>1200–6000 USD/yr"]
        D5[Insights reports<br/>B2B data product]
    end

    VENDOR((Vendor)) --> S1
    VENDOR --> S2
    VENDOR --> S3
    PARTNER((Bank / NGO / Enterprise)) --> S4
```

---

## Map 4 : How Money Flows (Ummah Economy → Taqdimah)

```mermaid
flowchart TD
    subgraph UMMah["The Ummah : Existing Spending"]
        UM1[Halal food & catering]
        UM2[Home services AC repair moving]
        UM3[Islamic education Quran teachers]
        UM4[Wedding & events]
        UM5[Professional services lawyers devs]
        UM6[Charity & waqf donations]
        UM7[Islamic finance needs]
    end

    UM1 & UM2 & UM3 & UM4 & UM5 --> SEARCH[User searches Taqdimah]
    UM6 --> INSTITUTION[Institution profiles]
    UM7 --> FINANCE[Islamic finance category]

    SEARCH --> VENDOR_TXN[Vendor serves customer<br/>off-platform or in-app]
    INSTITUTION --> DONATE[Donation via partner<br/>not Taqdimah wallet Phase 1]
    FINANCE --> REFER[Referral to Shariah bank<br/>Taqdimah never lends]

    VENDOR_TXN --> FEE1[Taqdimah earns:<br/>subscription / lead / commission]
    DONATE --> FEE2[Taqdimah earns:<br/>optional capped platform fee P3]
    REFER --> FEE3[Taqdimah earns:<br/>disclosed referral fee P3]

    FEE1 & FEE2 & FEE3 --> REINVEST[Reinvest in:<br/>trust + verification + BD team]

    style UMMah fill:#eafaf1,stroke:#27ae60
    style FEE1 fill:#fef9e7,stroke:#f39c12
    style FEE2 fill:#fef9e7,stroke:#f39c12
    style FEE3 fill:#fef9e7,stroke:#f39c12
```

**Taqdimah does not create new spending.** It **organizes and trusts** spending that already happens in WhatsApp groups and Facebook.

---

## Map 5 : Revenue by Platform Layer (What Enables What)

```mermaid
flowchart TB
    subgraph LAYERS["Platform Layer → Revenue Enabled"]
        direction LR
        L1[Identity Layer] --> R_NONE[No direct revenue<br/>enables trust]
        L2[Search Layer] --> R_SPON[R6 Sponsored search]
        L3[Discovery Layer] --> R_FEAT[R4 Featured listings]
        L4[Trust Layer] --> R_PRO[R2 Pro badge value<br/>verification = willingness to pay]
        L5[Reputation Layer] --> R_LEAD[R5 Better leads<br/>higher conversion]
        L6[Marketplace Layer] --> R_PPC[R5 Pay per lead<br/>R7 Booking fee]
        L7[Messaging Layer] --> R_PRO2[Pro plan stickiness]
        L8[Payment Layer] --> R_ESC[R7–R8 Commission + escrow]
        L9[AI Engine] --> R_AI[R14 AI copilot add-on]
        L10[Partner API] --> R_API[R12 Enterprise API]
    end
```

---

## Map 6 : Pricing Tiers vs Revenue (Vendor Side)

```mermaid
flowchart TD
    VENDOR_NEW[New vendor signs up FREE]

    VENDOR_NEW --> FREE[Free Plan<br/>0 BDT/mo]
    FREE --> F1[10 leads per month]
    FREE --> F2[Basic profile]
    FREE --> F3[No featured placement]

    FREE -->|gets value from 3+ leads| CONVERT{Upgrade?}

    CONVERT -->|20% convert| PRO[Pro Plan<br/>999 BDT/mo ~8 USD]
    CONVERT -->|5% convert| BIZ[Business Plan<br/>2499 BDT/mo ~20 USD]
    CONVERT -->|no| CHURN[Risk: churn<br/>outreach required]

    PRO --> P1[Unlimited leads]
    PRO --> P2[Analytics dashboard]
    PRO --> P3[Pro badge on profile]

    BIZ --> B1[Everything in Pro]
    BIZ --> B2[Featured slot rotation]
    BIZ --> B3[Multi-user staff accounts]
    BIZ --> B4[API read access]

    PRO --> ADDON1[+ Featured slot purchase<br/>1500–5000 BDT extra]
    BIZ --> ADDON2[+ Sponsored search CPC]

    PRO & BIZ --> REVENUE((Monthly Recurring Revenue))
    ADDON1 & ADDON2 --> REVENUE
```

---

## Map 7 : Lead Economics (Pay-Per-Lead Model)

```mermaid
sequenceDiagram
    participant U as Consumer
    participant A as Taqdimah
    participant V as Vendor
    participant B as Billing

    U->>A: Submit lead request FREE
    A->>V: Deliver qualified lead
    Note over V: Free plan: uses 1 of 10 monthly quota

    alt Free quota remaining
        V->>A: Receive lead at no charge
    else Free quota exhausted
        A->>B: Charge 50–500 BDT per lead
        B->>V: Invoice or block until payment
    end

    V->>U: Respond + win job
    U->>V: Pays vendor directly Phase 1
    Note over A,V: Phase 2: escrow through Taqdimah 5–12% fee
```

| Lead type | BDT per lead | Example |
|-----------|--------------|---------|
| Standard home service | 50–150 | AC repair, cleaning |
| Professional | 150–300 | Lawyer, accountant |
| High-value | 300–500 | Architect, developer |
| Event / catering | 200–400 | 100+ guest events |

---

## Map 8 : Transaction & Escrow Model (Phase 2)

```mermaid
stateDiagram-v2
    [*] --> QuoteSent: Vendor quotes 10000 BDT
    QuoteSent --> PaymentPending: User accepts
    PaymentPending --> EscrowHeld: SSLCommerz payment 10500 BDT
    note right of EscrowHeld: User pays 10000 + 500 platform fee shown upfront
    EscrowHeld --> JobInProgress: Vendor starts
    JobInProgress --> JobComplete: Vendor marks done
    JobComplete --> UserConfirm: User confirms OR 72h auto-release
    UserConfirm --> FundsReleased: 9000 to vendor + 1000 Taqdimah
    JobComplete --> Disputed: User disputes
    Disputed --> Refunded: Full refund
    Disputed --> FundsReleased: Admin resolves for vendor
    FundsReleased --> [*]
```

| Category | Commission | Why |
|----------|------------|-----|
| Home services | 8% | Standard marketplace |
| Professional | 10% | Higher ticket, more trust value |
| Islamic education | 5% | Community incentive |
| Catering / events | 10% | Coordination heavy |

---

## Map 9 : Islamic Finance & Waqf Revenue (Phase 3 : Halal Only)

```mermaid
flowchart TD
    subgraph HALAL["Permissible Revenue : Ummah Aligned"]
        H1[Referral fee from Islamic bank<br/>Murabaha / Musharakah products]
        H2[Takaful referral<br/>family + business policies]
        H3[Waqf campaign tooling<br/>capped fee max 5 percent disclosed]
        H4[Halal cert badge for restaurants<br/>verification service fee]
        H5[Scholar verified badge<br/>credential review fee]
    end

    subgraph HARAM["Never Allowed on Taqdimah"]
        X1[Interest-based loans APR]
        X2[Gambling / lottery]
        X3[Alcohol / haram goods categories]
        X4[Deceptive hidden fees]
        X5[Selling user data]
    end

    USER[Muslim user needs finance] --> H1
    USER2[Mosque fundraising] --> H3
    VENDOR_FOOD[Halal restaurant] --> H4
    SCHOLAR[Quran teacher] --> H5

    SHARIAH[Shariah Advisory Board<br/>reviews before launch] --> H1
    SHARIAH --> H3

    style HALAL fill:#eafaf1,stroke:#27ae60
    style HARAM fill:#fadbd8,stroke:#e74c3c
```

---

## Map 10 : Revenue Timeline (When Each Stream Goes Live)

```mermaid
gantt
    title Taqdimah Revenue Stream Activation
    dateFormat YYYY-MM
    axisFormat %b %Y

    section Phase 1 : Month 5+
    Free vendor tier           :done, 2026-07, 2026-12
    Pro subscription 999 BDT :2026-12, 2027-03
    Business 2499 BDT          :2027-01, 2027-06
    Featured listings          :2027-01, 2027-12
    Pay per lead overage       :2027-01, 2027-12
    Sponsored search           :2027-03, 2028-01

    section Phase 2 : Year 2
    Booking + escrow 5-12%     :2027-06, 2028-06
    Institution premium pages  :2027-09, 2028-06
    In-app messaging Pro lock  :2027-06, 2028-06

    section Phase 3 : Year 2-3
    Islamic finance referrals  :2028-01, 2029-01
    Waqf charity tools         :2028-03, 2029-06
    Enterprise API             :2028-06, 2029-12
    AI vendor copilot add-on   :2028-09, 2029-12
    Market insights B2B        :2029-01, 2030-01
```

---

## Map 11 : Revenue Mix Evolution (Year 1 → Year 5)

```mermaid
pie title Year 1 Revenue Mix
    "Vendor SaaS" : 40
    "Featured + Leads" : 45
    "Transactions" : 0
    "Finance + NGO" : 0
    "Enterprise API" : 15
```

```mermaid
pie title Year 3 Revenue Mix
    "Vendor SaaS" : 20
    "Featured + Leads" : 15
    "Transactions escrow" : 40
    "Finance + Waqf" : 15
    "Enterprise + Data" : 10
```

```mermaid
pie title Year 5 Revenue Mix target
    "Vendor SaaS" : 15
    "Featured + Ads" : 10
    "Transactions" : 45
    "Islamic finance + Waqf" : 20
    "Enterprise API + Data" : 10
```

| Year | ARR target | Primary driver |
|------|------------|----------------|
| Y1 | $15–25K | Subscriptions + featured |
| Y2 | $120–200K | Escrow commissions kick in |
| Y3 | $500K–1M | Transactions + finance referrals |
| Y5 | $2M+ | Full ecosystem |

---

## Map 12 : Unit Economics (One Vendor Lifecycle)

```mermaid
flowchart LR
    CAC[CAC<br/>500 BDT<br/>ecosystem marketing] --> SIGNUP[Free signup]
    SIGNUP --> LEADS[Receives 10 free leads]
    LEADS --> CONV{Converts to Pro<br/>within 90 days?}

    CONV -->|20% yes| PRO[Pro 999 BDT/mo]
    CONV -->|80% no| CHURN[Churn or stay free]

    PRO --> LTV[LTV Year 1<br/>~12,000 BDT ~100 USD]
    LTV --> RATIO[LTV:CAC = 24:1<br/>healthy]

    PRO --> UPSell[30% buy featured<br/>+2000 BDT/mo avg]
    UPSell --> LTV2[LTV with upsell<br/>~36,000 BDT]

    style RATIO fill:#eafaf1,stroke:#27ae60
```

---

## Map 13 : Network Effect → Revenue Flywheel

```mermaid
flowchart TD
    MORE_USERS[More users search] --> MORE_LEADS[More leads generated]
    MORE_LEADS --> VENDOR_VALUE[Vendors see ROI]
    VENDOR_VALUE --> MORE_VENDORS[More vendors join]
    MORE_VENDORS --> BETTER_RESULTS[Better search results]
    BETTER_RESULTS --> MORE_TRUST[More reviews + trust]
    MORE_TRUST --> MORE_USERS

    MORE_VENDORS --> MORE_COMPETITION[Vendors compete for visibility]
    MORE_COMPETITION --> PAY_FEATURED[Pay for featured slots]
    MORE_COMPETITION --> PAY_PRO[Upgrade to Pro]

    MORE_LEADS --> PAY_LEADS[Pay per lead overage]
    MORE_USERS --> PAY_TXN[Phase 2: transaction volume]

    PAY_FEATURED & PAY_PRO & PAY_LEADS & PAY_TXN --> REVENUE[Taqdimah Revenue grows]
    REVENUE --> INVEST[Better product + verification]
    INVEST --> MORE_TRUST
```

---

## Map 14 : Business Model Canvas (Visual)

```mermaid
flowchart TB
    subgraph KEY_PARTNERS["Key Partners"]
        KP1[Mosques & madaris]
        KP2[Islamic banks / Takaful]
        KP3[SSLCommerz / payments]
        KP4[iDEA / Startup Bangladesh]
        KP5[NGOs & waqf boards]
    end

    subgraph KEY_ACTIVITIES["Key Activities"]
        KA1[Verify vendors]
        KA2[Run search + ranking]
        KA3[Ecosystem marketing]
        KA4[Moderate trust]
    end

    subgraph VALUE["Value Propositions"]
        VP1[Consumers: one trusted search]
        VP2[Vendors: inbound halal leads]
        VP3[Ummah: ethical discovery layer]
    end

    subgraph CUSTOMER_REL["Customer Relationships"]
        CR1[Self-serve search]
        CR2[Vendor dashboard]
        CR3[Community + WhatsApp]
    end

    subgraph SEGMENTS["Customer Segments"]
        CS1[Muslim consumers BD]
        CS2[SMEs + freelancers]
        CS3[Islamic service providers]
        CS4[Institutions]
    end

    subgraph KEY_RESOURCES["Key Resources"]
        KR1[Trust data + reviews]
        KR2[Category taxonomy]
        KR3[Brand Open Taqdimah]
        KR4[Verification ops]
    end

    subgraph CHANNELS["Channels"]
        CH1[SEO city+category pages]
        CH2[Facebook ecosystem posts]
        CH3[Mosque QR flyers]
        CH4[Word of mouth]
    end

    subgraph COST["Cost Structure"]
        CO1[Infra 50 to 100 USD/mo]
        CO2[AI API 50 to 70 USD/mo]
        CO3[Founder time sweat equity]
        CO4[Moderator Month 6+]
    end

    subgraph REVENUE["Revenue Streams"]
        REV1[SaaS subscriptions]
        REV2[Featured + sponsored]
        REV3[Pay per lead]
        REV4[Transaction commission]
        REV5[Finance + waqf fees]
        REV6[Enterprise API]
    end

    KEY_PARTNERS --> KEY_ACTIVITIES
    KEY_ACTIVITIES --> VALUE
    VALUE --> CUSTOMER_REL
    CUSTOMER_REL --> SEGMENTS
    KEY_RESOURCES --> KEY_ACTIVITIES
    CHANNELS --> SEGMENTS
    KEY_ACTIVITIES --> COST
    SEGMENTS --> REVENUE
```

---

## Map 15 : Competitive Revenue Positioning

```mermaid
quadrantChart
    title "Revenue Model Positioning"
    x-axis "Low Take Rate" --> "High Take Rate"
    y-axis "Low Trust" --> "High Trust"
    quadrant-1 "Premium trusted marketplace"
    quadrant-2 "High fee low trust - avoid"
    quadrant-3 "Low fee commodity"
    quadrant-4 "Trust leader fair fees - Taqdimah target"
    Bikroy: [0.2, 0.25]
    Sheba.xyz: [0.45, 0.55]
    Facebook Groups: [0.05, 0.15]
    Google Maps: [0.1, 0.4]
    Taqdimah Year 1: [0.35, 0.75]
    Taqdimah Year 3: [0.5, 0.9]
    Grab super app: [0.85, 0.6]
```

**Taqdimah target quadrant:** High trust + moderate fair fees (not the cheapest, not extractive).

---

## Map 16 : Possible vs Planned (Everything You CAN Do)

| # | Revenue model | Phase | Status | Halal fit |
|---|---------------|-------|--------|-----------|
| 1 | Free vendor tier (funnel) | P1 | Planned | Yes |
| 2 | Pro SaaS 999 BDT/mo | P1 | Planned | Yes |
| 3 | Business SaaS 2499 BDT/mo | P1 | Planned | Yes |
| 4 | Featured category slots | P1 | Planned | Yes : if labeled |
| 5 | City homepage banners | P1 | Planned | Yes : if labeled |
| 6 | Sponsored search CPC | P1 | Planned | Yes : if labeled |
| 7 | Pay-per-lead | P1 | Planned | Yes : wasīlah |
| 8 | Booking commission 5–12% | P2 | Planned | Yes : ju'ālah |
| 9 | Escrow payment processing | P2 | Planned | Yes : disclosed |
| 10 | Institution premium pages | P2 | Planned | Yes |
| 11 | In-app messaging (Pro gate) | P2 | Planned | Yes |
| 12 | Halal certification badge fee | P2 | Possible | Yes |
| 13 | Scholar verification fee | P2 | Possible | Yes |
| 14 | Islamic finance referrals | P3 | Planned | Yes : Shariah review |
| 15 | Takaful referrals | P3 | Possible | Yes |
| 16 | Waqf campaign platform fee | P3 | Planned | Yes : capped |
| 17 | NGO donation tooling | P3 | Possible | Yes : transparent |
| 18 | Enterprise API licensing | P3 | Planned | Yes |
| 19 | White-label search widget | P3 | Possible | Yes |
| 20 | Market insights reports | P3 | Possible | Yes |
| 21 | AI vendor copilot add-on | P3 | Possible | Yes |
| 22 | Recruitment / job listings | P4 | Possible | Yes |
| 23 | Halal product marketplace | P4 | Possible | Yes |
| 24 | Event ticketing (Islamic) | P4 | Possible | Yes |
| 25 | Training course marketplace | P4 | Possible | Yes |
| 26 | Affiliate halal products | P4 | Possible | Yes : no haram |
| 27 | Data licensing anonymized | P4 | Possible | Yes : privacy |
| 28 | Franchise listing fees | P4 | Possible | Yes |

**28 possible streams. MVP needs only #1–7.**

---

## Map 17 : Revenue Decision Tree (What to launch when)

```mermaid
flowchart TD
    START((Revenue decision))

    START --> Q1{MVP live with<br/>100+ vendors?}
    Q1 -->|No| WAIT[Focus free tier only<br/>no monetization yet]
    Q1 -->|Yes| Q2{Vendors getting<br/>leads consistently?}

    Q2 -->|No| FIX[Fix discovery + supply first]
    Q2 -->|Yes| Q3{500+ vendors<br/>5K MAU?}

    Q3 -->|No| SOFT[Soft launch Pro plan<br/>to top 20 vendors only]
    Q3 -->|Yes| LAUNCH[Full monetization:<br/>Pro + Featured + Pay-per-lead]

    LAUNCH --> Q4{Payments infra ready?}
    Q4 -->|Yes| ESCROW[Add escrow commission]
    Q4 -->|No| SAAS[Stay SaaS + leads revenue]

    ESCROW --> Q5{Shariah board approved?}
    Q5 -->|Yes| FINANCE[Add Islamic finance referrals]
    Q5 -->|No| WAIT2[Wait : do not launch finance]

    style WAIT fill:#eafaf1
    style FINANCE fill:#fef9e7
    style WAIT2 fill:#fadbd8
```

---

## Summary : All Revenue Through One Platform

```mermaid
flowchart TB
    Taqdimah((Taqdimah Platform))

    Taqdimah --> B2B[B2B : Vendors pay]
    Taqdimah --> B2B2[B2B : Partners pay]
    Taqdimah --> B2C_FREE[B2C : Users free always]

    B2B --> B1[Subscriptions]
    B2B --> B2[Featured ads]
    B2B --> B3[Pay per lead]
    B2B --> B4[Transaction %]

    B2B2 --> P1[Bank referrals]
    B2B2 --> P2[Enterprise API]
    B2B2 --> P3[NGO / waqf tools]

    B2C_FREE --> U1[Search forever free]
    B2C_FREE --> U2[Builds network effect]
    U2 --> B2

    B1 & B2 & B3 & B4 & P1 & P2 & P3 --> GOAL[Sustainable ethical<br/>infrastructure for<br/>the Muslim economy]
```

---

**Read next:** [BUSINESS_PLAN.md](./BUSINESS_PLAN.md) (full narrative) · [GUIDELINE_MAP.md](./GUIDELINE_MAP.md) · [PRD.md](./PRD.md)