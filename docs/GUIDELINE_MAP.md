# Taqdimah : Master Guideline Map (Mermaid)

> **How to read this:** Start at `START` in Diagram 1. Follow arrows. Cross-reference [SETUP_AND_TOOLS.md](./SETUP_AND_TOOLS.md) and [founders-kit README](../../README.md) at each `FK` node.

---

## Diagram 1 : Complete Journey (Idea → Global Platform)

```mermaid
flowchart TD
    START((START<br/>You + founders-kit repo))

    subgraph PHASE0["PHASE 0 : FOUNDATION (Week 1–2)"]
        direction TB
        P0A[Clone founders-kit repo]
        P0B[Read Taqdimah/README.md]
        P0C[Read founders-kit/README.md<br/>Bookmark tool directory]
        P0D[Read PRD.md + PRD-TECHNICAL.md]
        P0E[Read BUSINESS_PLAN.md]
        P0F[Read SETUP_AND_TOOLS.md]
        P0G[Read GUIDELINE_MAP.md<br/>this file]
        P0H[Create accounts:<br/>GitHub, Supabase, Vercel,<br/>OpenAI, PostHog, Sentry, Figma]
        P0I[Set $200/mo budget cap<br/>on OpenAI + tools]
        P0J[Setup Notion workspace<br/>vendor pipeline + content calendar]
        P0A --> P0B --> P0C --> P0D --> P0E --> P0F --> P0G --> P0H --> P0I --> P0J
    end

    START --> P0A

    subgraph PHASE1["PHASE 1 : BUILD MVP (Month 1–3)"]
        direction TB
        P1A[ALD-001: Next.js scaffold<br/>Tool: Cursor]
        P1B[ALD-002: Supabase schema<br/>Tool: Supabase CLI]
        P1C[ALD-003: Seed 50 categories<br/>BN + EN + Islamic branch]
        P1D[ALD-004: Phone OTP Auth<br/>Tool: Supabase Auth]
        P1E[ALD-005: Search API + UI<br/>Tool: OpenAI mini + PostgreSQL FTS]
        P1F[ALD-006: Vendor public profile<br/>Tool: v0.dev + Figma]
        P1G[ALD-007: Lead request flow<br/>Tool: Resend email]
        P1H[ALD-008: Vendor dashboard]
        P1I[ALD-009: Verification workflow<br/>L2 identity + L3 business]
        P1J[ALD-010: Reviews + trust score]
        P1K[ALD-011: Admin panel]
        P1L[ALD-012: SEO city+category pages<br/>Dhaka, Ctg, Sylhet]
        P1M[Deploy production<br/>Tool: Vercel]
        P1N[PostHog + Clarity live]
        P1A --> P1B --> P1C --> P1D --> P1E --> P1F --> P1G --> P1H
        P1H --> P1I --> P1J --> P1K --> P1L --> P1M --> P1N
    end

    P0J --> P1A

    subgraph PHASE2["PHASE 2 : SEED SUPPLY (Month 1–4 parallel)"]
        direction TB
        P2A[Google Maps: find vendors<br/>10 categories × 10 each]
        P2B[Airtable pipeline:<br/>found → contacted → verified]
        P2C[WhatsApp outreach:<br/>free verified profile pitch]
        P2D[Loom video: how to claim profile]
        P2E[Mosque QR flyers<br/>Tool: Canva]
        P2F[Admin CSV bulk import<br/>100 seed vendors]
        P2G[Manual verification<br/>48h SLA]
        P2H[Target: 100 vendors Month 2<br/>500 vendors Month 6]
        P2A --> P2B --> P2C --> P2D --> P2E --> P2F --> P2G --> P2H
    end

    P1D --> P2A
    P2H --> P1N

    subgraph PHASE3["PHASE 3 : SEED DEMAND (Month 3–5)"]
        direction TB
        P3A[Ecosystem marketing<br/>NOT download Taqdimah posts]
        P3B[Facebook groups:<br/>real demand stories]
        P3C[Buffer schedule posts<br/>3–5 per week]
        P3D[SEO pages ranking<br/>Google Search Console]
        P3E[Startup Bangladesh Discord<br/>beta users]
        P3F[Typeform user surveys<br/>what categories missing]
        P3G[Target: 5K MAU Month 6]
        P3A --> P3B --> P3C --> P3D --> P3E --> P3F --> P3G
    end

    P1L --> P3A
    P2H --> P3A

    subgraph PHASE4["PHASE 4 : AUTOMATE (Month 3–5)"]
        direction TB
        P4A[Setup n8n self-hosted]
        P4B[Workflow: lead → WhatsApp vendor]
        P4C[Workflow: lead → email user]
        P4D[Workflow: verification → Telegram you]
        P4E[Workflow: nightly vendor digest]
        P4F[Trigger.dev: trust score worker]
        P4G[Trigger.dev: search index refresh]
        P4H[UptimeRobot monitoring]
        P4A --> P4B --> P4C --> P4D --> P4E --> P4F --> P4G --> P4H
    end

    P1N --> P4A

    subgraph PHASE5["PHASE 5 : MONETIZE (Month 5–6)"]
        direction TB
        P5A[Launch Pro plan 999 BDT/mo<br/>Tool: SSLCommerz]
        P5B[Launch Business plan 2499 BDT/mo]
        P5C[Featured listings slots<br/>max 3 per category+city]
        P5D[Pay-per-lead overage fees]
        P5E[Target: 25 Pro + 10 Business<br/>$3K MRR]
        P5F[Apply iDEA grant BDT 10L<br/>Tool: idea.gov.bd]
        P5A --> P5B --> P5C --> P5D --> P5E --> P5F
    end

    P3G --> P5A
    P4H --> P5A

    subgraph PHASE6["PHASE 6 : GROW (Month 6–12)"]
        direction TB
        P6A[In-app messaging P2]
        P6B[AI intent bundles<br/>moving, wedding, ramadan]
        P6C[SSLCommerz escrow payments]
        P6D[Institution profiles<br/>mosques, NGOs]
        P6E[Expand Chattogram + Sylhet<br/>full category coverage]
        P6F[Product Hunt launch]
        P6G[Apply Startup Bangladesh seed]
        P6H[Target: 1000 vendors, 1K MRR]
        P6A --> P6B --> P6C --> P6D --> P6E --> P6F --> P6G --> P6H
    end

    P5E --> P6A

    subgraph PHASE7["PHASE 7 : GLOBAL (Year 2+)"]
        direction TB
        P7A[Malaysia + Indonesia pilot]
        P7B[Arabic + Malay UI]
        P7C[Islamic finance referrals<br/>Shariah board review]
        P7D[Waqf + charity module]
        P7E[Partner API marketplace]
        P7F[Stripe global payments]
        P7G[Target: 5 countries, 100K listings]
        P7A --> P7B --> P7C --> P7D --> P7E --> P7F --> P7G
    end

    P6H --> P7A

    P7G --> END((END STATE<br/>Open Taqdimah =<br/>Muslim economy gateway))

    FK0[founders-kit/README.md<br/>Tools at every phase] -.-> P0C
    FK0 -.-> P2C
    FK0 -.-> P3B
    FK0 -.-> P5F
```

---

## Diagram 2 : One-Man Army Daily Map (12 Hours)

```mermaid
flowchart TD
    WAKE((6:00 AM<br/>Wake up))

    subgraph MORNING["MORNING : BUILD (6:00–12:00)"]
        direction TB
        M1[6:00–6:30<br/>Read PROGRESS.md + TASKS.md<br/>Pick 1 task max]
        M2[6:30–7:00<br/>Claude: plan task from PRD-TECHNICAL]
        M3[7:00–10:00<br/>Cursor Agent: implement task<br/>Deep work : phone DND]
        M4[10:00–10:30<br/>Break + git diff review]
        M5[10:30–12:00<br/>Cursor: finish task OR fix bugs<br/>Run npm test + build]
        M1 --> M2 --> M3 --> M4 --> M5
    end

    WAKE --> M1

    subgraph MIDDAY["MIDDAY : BREAK (12:00–13:00)"]
        MID[Eat + pray + no screens]
    end

    M5 --> MID

    subgraph AFTERNOON["AFTERNOON : VENDORS + OPS (13:00–18:00)"]
        direction TB
        A1[13:00–14:00<br/>Vendor outreach<br/>WhatsApp + Airtable update<br/>Target: 10 contacts/day]
        A2[14:00–15:00<br/>Verification reviews<br/>Admin panel approve/reject]
        A3[15:00–16:00<br/>Deploy + monitor<br/>Vercel + Sentry + PostHog]
        A4[16:00–17:00<br/>Ecosystem marketing<br/>Canva + Buffer + FB groups]
        A5[17:00–18:00<br/>User feedback<br/>Crisp + Canny + surveys]
        A1 --> A2 --> A3 --> A4 --> A5
    end

    MID --> A1

    subgraph EVENING["EVENING : LEARN + PLAN (18:00–22:00)"]
        direction TB
        E1[18:00–19:00<br/>Dinner + break]
        E2[19:00–20:00<br/>Research block<br/>Perplexity + founders-kit README]
        E3[20:00–21:00<br/>Write tomorrow Cursor prompt<br/>Update PROGRESS.md]
        E4[21:00–22:00<br/>YC videos / BD ecosystem<br/>Or n8n workflow tweaks]
        E1 --> E2 --> E3 --> E4
    end

    A5 --> E1

    E4 --> SLEEP((22:00<br/>Sleep<br/>8h rest = non-negotiable))

    subgraph TOOLS_DAILY["Tools used today"]
        T1[Cursor]
        T2[Claude]
        T3[WhatsApp Business]
        T4[Airtable]
        T5[Vercel + Sentry]
        T6[PostHog + Clarity]
        T7[Canva + Buffer]
        T8[Notion]
        T9[founders-kit README]
    end

    M3 -.-> T1
    M2 -.-> T2
    A1 -.-> T3
    A1 -.-> T4
    A3 -.-> T5
    A3 -.-> T6
    A4 -.-> T7
    E3 -.-> T8
    E2 -.-> T9
```

---

## Diagram 3 : Technical Build Map (Engineering Path)

```mermaid
flowchart LR
    subgraph LAYERS["Platform Layers : Build Order"]
        direction TB
        L1[1. Identity Layer<br/>Supabase Auth OTP]
        L2[2. Catalog Layer<br/>Categories + cities seed]
        L3[3. Vendor Layer<br/>Profiles + portfolio]
        L4[4. Trust Layer<br/>Verification L2-L4]
        L5[5. Search Layer<br/>Intent parser + FTS]
        L6[6. Discovery Layer<br/>Ranking + featured]
        L7[7. Marketplace Layer<br/>Leads + routing]
        L8[8. Reputation Layer<br/>Reviews + trust score]
        L9[9. Monetization Layer<br/>Plans + featured slots]
        L10[10. Admin Layer<br/>Moderation + import]
        L1 --> L2 --> L3 --> L4 --> L5 --> L6 --> L7 --> L8 --> L9 --> L10
    end

    subgraph FUTURE["Phase 2+ Layers"]
        direction TB
        F1[11. Messaging Layer]
        F2[12. Payment Escrow Layer<br/>SSLCommerz]
        F3[13. AI Bundle Layer<br/>life events]
        F4[14. Institution Layer<br/>mosques NGOs]
        F5[15. Partner API Layer]
        F1 --> F2 --> F3 --> F4 --> F5
    end

    L10 --> F1

    subgraph DOCS["Read before coding each layer"]
        D1[PRD-TECHNICAL.md]
        D2[DATA_MODEL.md]
        D3[API_REFERENCE.md]
        D4[SEARCH_RANKING.md]
        D5[TRUST_SYSTEM.md]
        D6[SYSTEM_FLOWS.md]
    end

    L5 -.-> D4
    L4 -.-> D5
    L7 -.-> D6
    L1 -.-> D2
```

---

## Diagram 4 : User & Vendor Flywheel Map

```mermaid
flowchart TD
    subgraph DEMAND["Consumer Side"]
        D1[User has need<br/>architect, quran teacher, catering]
        D2[Opens Taqdimah / SEO page / FB post link]
        D3[Natural language search<br/>Bengali or English]
        D4[See ranked verified vendors<br/>trust score + reviews]
        D5[View vendor profile]
        D6[Submit lead request]
        D7[Receive vendor response]
        D8[Complete service off-platform Phase 1]
        D9[Leave review]
        D10[Return + refer friends]
        D1 --> D2 --> D3 --> D4 --> D5 --> D6 --> D7 --> D8 --> D9 --> D10
        D10 --> D1
    end

    subgraph SUPPLY["Vendor Side"]
        S1[Vendor sees ecosystem demand post<br/>or competitor on Taqdimah]
        S2[Registers at /register/vendor]
        S3[Creates profile 60%+ complete]
        S4[Submits L2 + L3 verification docs]
        S5[Admin approves within 48h]
        S6[Profile live in search index]
        S7[Receives free leads monthly quota]
        S8[Responds quickly → trust score up]
        S9[Gets reviews → more visibility]
        S10[Upgrades Pro plan]
        S1 --> S2 --> S3 --> S4 --> S5 --> S6 --> S7 --> S8 --> S9 --> S10
        S10 --> S6
    end

    D6 -->|lead notification| S7
    S8 -->|response| D7
    D9 -->|review| S9

    subgraph PLATFORM["Taqdimah Platform Value"]
        P1[Discovery]
        P2[Trust]
        P3[Leads]
        P4[Revenue]
    end

    D4 --> P1
    S5 --> P2
    D6 --> P3
    S10 --> P4
```

---

## Diagram 5 : Ecosystem Marketing Map (Chicken & Egg Solver)

```mermaid
flowchart TD
    PROBLEM((Chicken & Egg<br/>No users without vendors<br/>No vendors without users))

    subgraph MARKET_DEMAND["Market the NEED not the APP"]
        MD1[Post: Someone in Sylhet<br/>needs trusted architect]
        MD2[Post: Dhaka startup needs<br/>React developer]
        MD3[Post: Family needs halal<br/>catering 200 guests Uttara]
        MD4[Post: Mosque needs<br/>verified electrician]
        MD5[SEO page ranks:<br/>/dhaka/quran-teachers]
    end

    PROBLEM --> MD1
    PROBLEM --> MD2
    PROBLEM --> MD3
    PROBLEM --> MD4
    PROBLEM --> MD5

    MD1 --> VENDOR_CURIOUS[Vendor asks:<br/>where are these leads from?]
    MD2 --> VENDOR_CURIOUS
    MD3 --> VENDOR_CURIOUS
    MD4 --> VENDOR_CURIOUS
    MD5 --> USER_FOUND[User finds answer<br/>on Taqdimah]

    VENDOR_CURIOUS --> SIGNUP[Vendor signs up free]
    SIGNUP --> VERIFY[Gets verified]
    VERIFY --> MORE_SUPPLY[More supply in search]
    MORE_SUPPLY --> USER_FOUND
    USER_FOUND --> MORE_DEMAND[More user searches + leads]
    MORE_DEMAND --> MD1

    subgraph CHANNELS["Channels : Tool per channel"]
        CH1[Facebook groups<br/>Tool: Buffer]
        CH2[WhatsApp communities<br/>Tool: manual share]
        CH3[Mosque notice board<br/>Tool: Canva QR]
        CH4[LinkedIn<br/>Tool: Buffer]
        CH5[Google SEO<br/>Tool: Search Console]
        CH6[Startup Bangladesh Discord<br/>Tool: Discord]
        CH7[Product Hunt<br/>Tool: PH Ship]
    end

    MD1 -.-> CH1
    MD2 -.-> CH4
    MD3 -.-> CH1
    MD4 -.-> CH3
    MD5 -.-> CH5
```

---

## Diagram 6 : Revenue & Ummah Monetization Map

```mermaid
flowchart TD
    UMMAH((Muslim Economy<br/>$2T+ global spending))

    UMMAH --> DISCOVER[Taqdimah organizes<br/>existing halal spending]
    DISCOVER --> TRANSPARENT[Transparent fees only<br/>No riba, no gharar]

    subgraph REV_P1["Phase 1 Revenue : Month 5+"]
        R1[Vendor Pro SaaS<br/>999 BDT/mo]
        R2[Vendor Business SaaS<br/>2499 BDT/mo]
        R3[Featured listings<br/>1500–5000 BDT/mo]
        R4[Pay-per-lead<br/>50–500 BDT]
    end

    TRANSPARENT --> R1
    TRANSPARENT --> R2
    TRANSPARENT --> R3
    TRANSPARENT --> R4

    subgraph REV_P2["Phase 2 Revenue : Year 2"]
        R5[Booking commission 5–12%<br/>SSLCommerz escrow]
        R6[Sponsored search CPC<br/>always labeled]
    end

    R1 --> R5
    R4 --> R6

    subgraph REV_P3["Phase 3 Revenue : Year 2–3"]
        R7[Islamic finance referrals<br/>Murabaha, Takaful only]
        R8[Waqf + charity tools<br/>capped platform fee]
        R9[Enterprise API<br/>$1200–6000/yr]
        R10[Market insights reports]
    end

    R5 --> R7
    R5 --> R8
    R6 --> R9
    R7 --> R10

    subgraph GUARDRAILS["Shariah Guardrails"]
        G1[No riba products listed]
        G2[Sponsored always labeled]
        G3[Haram categories blocked]
        G4[Fees disclosed upfront]
        G5[Scholar verify L4 providers]
        G6[Shariah board before finance module]
    end

    TRANSPARENT --> G1
    TRANSPARENT --> G2
    TRANSPARENT --> G3
    TRANSPARENT --> G4
    R7 --> G5
    R7 --> G6

    R10 --> GOAL((Goal: Sustainable<br/>ethical infrastructure<br/>for the Ummah))
```

---

## Diagram 7 : Tool Selection Decision Map

```mermaid
flowchart TD
    NEED((I need something))

    NEED --> Q1{What type?}

    Q1 -->|Write code| CODE[Use Cursor<br/>$20/mo]
    Q1 -->|Plan/review architecture| ARCH[Use Claude<br/>free–$20]
    Q1 -->|Research competitor/docs| RESEARCH[Use Perplexity<br/>free]
    Q1 -->|Generate UI component| UI[Use v0.dev + Figma<br/>free]
    Q1 -->|Store data + auth| DB[Use Supabase<br/>free–$25]
    Q1 -->|Deploy website| DEPLOY[Use Vercel<br/>free–$20]
    Q1 -->|Send email alerts| EMAIL[Use Resend<br/>free 3k/mo]
    Q1 -->|Track users| ANALYTICS[Use PostHog + Clarity<br/>free]
    Q1 -->|Automate workflows| AUTO[Use n8n<br/>free self-host]
    Q1 -->|Contact vendors| WA[Use WhatsApp Business<br/>free]
    Q1 -->|Track vendor pipeline| PIPE[Use Airtable<br/>free]
    Q1 -->|Accept payments BD| PAY[Use SSLCommerz<br/>per txn]
    Q1 -->|Schedule social posts| SOCIAL[Use Buffer + Canva<br/>free]
    Q1 -->|Find any other tool| FK[Open founders-kit/README.md<br/>Cmd+F search]

    CODE --> BUDGET{Still under<br/>$200/mo?}
    ARCH --> BUDGET
    DB --> BUDGET
    PAY --> BUDGET

    BUDGET -->|Yes| OK[Approved : use it]
    BUDGET -->|No| REPLACE[Find free alternative<br/>in founders-kit README<br/>or SETUP_AND_TOOLS Section 13]

    FK --> OK
```

---

## Diagram 8 : Agentic AI Development Map (Cursor Workflow)

```mermaid
flowchart TD
    START_AGENT((Start coding session))

    START_AGENT --> READ1[Agent reads README.md]
    READ1 --> READ2[Agent reads PRD-TECHNICAL.md]
    READ2 --> READ3[Agent reads DATA_MODEL.md]
    READ3 --> READ4[Agent picks TASK from TASKS.md]
    READ4 --> PLAN[Claude plans implementation<br/>acceptance criteria check]

    PLAN --> IMPLEMENT[Cursor implements<br/>50–300 lines max]
    IMPLEMENT --> TEST[Run npm test + build]
    TEST --> PASS{Passes?}

    PASS -->|No| FIX[Cursor fixes errors<br/>max 3 retries]
    FIX --> TEST

    PASS -->|Yes| REVIEW[You review diff<br/>30–60 min]
    REVIEW --> GOOD{Approve?}

    GOOD -->|No| FEEDBACK[Give agent specific feedback]
    FEEDBACK --> IMPLEMENT

    GOOD -->|Yes| MERGE[Git commit + push]
    MERGE --> DEPLOY[Vercel auto deploy]
    DEPLOY --> PROGRESS[Update PROGRESS.md]
    PROGRESS --> SENTRY[Check Sentry errors]
    SENTRY --> POSTHOG[Check PostHog events]
    POSTHOG --> NEXT[Pick next TASK tomorrow]

    subgraph NEVER["Agent must NEVER"]
        N1[Add paid tool without approval]
        N2[Skip trust-gated search rule]
        N3[Build Phase 2 before P0 done]
        N4[Expose service role key client-side]
        N5[Skip PROGRESS.md update]
    end

    IMPLEMENT -.-> NEVER
```

---

## Diagram 9 : Bangladesh Funding Path Map

```mermaid
flowchart LR
    subgraph NOW["Now : Bootstrap"]
        B1[Personal savings<br/>$200/mo tools]
        B2[Build MVP<br/>500 vendors 5K MAU]
    end

    subgraph MONTH4["Month 4–5 : Grant"]
        G1[Register RJSC<br/>+ Trade License]
        G2[Apply iDEA<br/>BDT 10 Lakh non-equity]
        G2 --> G3[Use grant for:<br/>marketing + moderator]
    end

    subgraph MONTH6["Month 6–9 : Seed"]
        S1[Pitch Startup Bangladesh Ltd<br/>BDT 25L–5Cr equity]
        S2[Bangladesh Angels Network]
    end

    subgraph YEAR2["Year 2 : Scale"]
        Y1[Anchorless / SEA VC]
        Y2[Islamic impact funds]
        Y3[Stripe Atlas US entity<br/>if going global]
    end

    B1 --> B2 --> G1 --> G2 --> G3 --> S1 --> S2 --> Y1 --> Y2 --> Y3

    FK_BD[founders-kit README<br/>Bangladesh Ecosystem section] -.-> G1
    FK_BD -.-> G2
    FK_BD -.-> S1
```

---

## Diagram 10 : Document Navigation Map (What to Read When)

```mermaid
flowchart TD
    Q((What do I need?))

    Q -->|Understand vision| A1[PRD.md]
    Q -->|Engineering spec| A2[PRD-TECHNICAL.md]
    Q -->|Setup + tools| A3[SETUP_AND_TOOLS.md]
    Q -->|This guideline map| A4[GUIDELINE_MAP.md]
    Q -->|Database schema| A5[DATA_MODEL.md]
    Q -->|API endpoints| A6[API_REFERENCE.md]
    Q -->|Feature acceptance| A7[FEATURES.md]
    Q -->|System flows| A8[SYSTEM_FLOWS.md]
    Q -->|Search algorithm| A9[SEARCH_RANKING.md]
    Q -->|Trust + verification| A10[TRUST_SYSTEM.md]
    Q -->|Revenue + GTM| A11[BUSINESS_PLAN.md]
    Q -->|Revenue diagrams all 17| A21[REVENUE_MODEL_MAP.md]
    Q -->|AI bundles Phase 2| A12[AI_ENGINE.md]
    Q -->|Payments Phase 2| A13[PAYMENTS_ESCROW.md]
    Q -->|What to code next| A14[TASKS.md]
    Q -->|Build status| A15[PROGRESS.md]
    Q -->|Find external tool| A16[founders-kit/README.md]
    Q -->|Architecture overview| A17[ARCHITECTURE.md]
    Q -->|Service design| A18[TECHNICAL_DESIGN.md]
    Q -->|Why we chose X| A19[DECISIONS.md]
    Q -->|Events async| A20[EVENTS.md]

    A3 --> A16
    A14 --> A2
    A14 --> A5
```

---

## Diagram 11 : Master Map (Single Page Overview)

```mermaid
flowchart TB
    classDef phase fill:#e8f4f8,stroke:#2980b9
    classDef tool fill:#fef9e7,stroke:#f39c12
    classDef doc fill:#eafaf1,stroke:#27ae60
    classDef goal fill:#f4ecf7,stroke:#8e44ad

    YOU((👤 You<br/>Solo Founder<br/>12h/day · $200/mo))

    YOU --> FK[📚 founders-kit/README.md<br/>Tool Directory]
    YOU --> DOCS[📁 Taqdimah/docs/*<br/>Specifications]

    FK --> SETUP[SETUP_AND_TOOLS.md]
    DOCS --> GUIDE[GUIDELINE_MAP.md]

    SETUP --> BUILD
    GUIDE --> BUILD

    subgraph BUILD["🔨 BUILD"]
        BUILD1[Cursor + Next.js + Supabase]
        BUILD2[Search + Trust + Leads]
        BUILD3[Vercel Deploy]
    end

    subgraph SUPPLY["🏪 SUPPLY"]
        SUP1[Google Maps + WhatsApp]
        SUP2[Airtable 500 vendors]
        SUP3[Admin verify + import]
    end

    subgraph DEMAND["📣 DEMAND"]
        DEM1[Ecosystem FB posts]
        DEM2[SEO city pages]
        DEM3[Buffer + Canva]
    end

    subgraph AUTO["⚙️ AUTOMATE"]
        AUT1[n8n workflows]
        AUT2[PostHog + Sentry]
        AUT3[Resend + WhatsApp alerts]
    end

    subgraph MONEY["💰 MONETIZE"]
        MON1[SSLCommerz Pro plans]
        MON2[Featured listings]
        MON3[iDEA grant → SBDL]
    end

    subgraph SCALE["🌍 SCALE"]
        SCA1[AI bundles]
        SCA2[Escrow payments]
        SCA3[MY + ID + PK expand]
    end

    BUILD --> SUPPLY
    BUILD --> DEMAND
    SUPPLY --> AUTO
    DEMAND --> AUTO
    AUTO --> MONEY
    MONEY --> SCALE

    SCALE --> VISION

    VISION((🌙 VISION<br/>Open Taqdimah<br/>= Muslim economy OS)):::goal

    BUILD1:::phase
    SUP2:::tool
    DOCS:::doc
    FK:::doc
```

---

## How to Use This Map

| If you are… | Start at diagram |
|-------------|------------------|
| New : just starting | Diagram 1 (full journey) |
| Planning today | Diagram 2 (daily 12h) |
| Coding | Diagram 3 + Diagram 8 |
| Getting vendors | Diagram 4 + Diagram 5 |
| Planning revenue | Diagram 6 |
| Choosing a tool | Diagram 7 |
| Fundraising in BD | Diagram 9 |
| Lost in docs | Diagram 10 |
| Need one-page overview | Diagram 11 |

---

**Related:** [SETUP_AND_TOOLS.md](./SETUP_AND_TOOLS.md) · [README.md](../README.md) · [founders-kit README](../../README.md)