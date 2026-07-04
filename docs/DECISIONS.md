# Taqdimah : Architecture Decision Records (ADR)

---

## ADR-001: Only What Is Good for the Ummah (Purity Filter)

**Date:** 2026-07-04  
**Status:** Accepted

**Decision:** Taqdimah will **only** facilitate, list, promote or connect to things, knowledge, services, and people that are clearly good and beneficial for the Ummah. We actively exclude anything that is not a net positive for faith, family, community, or dignified halal living.

**Rationale:** This is the core of the gift to the Khalifah for societal islah. Nothing that weakens or distracts the Ummah is put out.

---

## ADR-002: Platform Nature (Updated)

**Date:** 2026-07-04  
**Status:** Accepted

**Decision:** Taqdimah is a pure gift infrastructure (discovery + trust + knowledge + coordination layers). Participants remain independent. We only surface beneficial providers and content. Taqdimah does not operate services or push anything non-beneficial.

**Rationale:** Preserves the purity of the offering. Focus is on real benefit to the Ummah, not volume or extraction.

---

## ADR-002: Market Entry

**Date:** 2026-07-03  
**Status:** Accepted

**Decision:** Launch in **Bangladesh** (Dhaka → Chattogram → Sylhet) before Malaysia/Indonesia/Pakistan.

**Rationale:** Founder market knowledge, iDEA grant path, 170M population, fragmented discovery problem acute.

---

## ADR-003: Sustenance for Workers (Only from Beneficial Activity)

**Date:** 2026-07-04  
**Status:** Accepted

**Decision:** Any support for the workers comes only from activity around things that are good and beneficial for the Ummah. Modest, transparent contributions from those who gain clear value. Free tier for knowledge seekers and small beneficial efforts is protected.

**Rationale:** The gift must stay pure. Workers are sustained so they can serve the Ummah with excellence and without compromise.

---

## ADR-004: Tech Stack

**Date:** 2026-07-03  
**Status:** Accepted

**Decision:** Next.js 15 + Supabase + Vercel + OpenAI mini for intent.

**Rationale:** SEO-critical, low ops, fits $200/mo budget, fast solo-founder iteration.

---

## ADR-005: Search v1

**Date:** 2026-07-03  
**Status:** Accepted

**Decision:** PostgreSQL full-text search + rule-based intent parser. LLM fallback only when confidence < 0.7.

**Rationale:** Cost control. Most BD queries map to finite category dictionary.

---

## ADR-006: Trust Before Volume

**Date:** 2026-07-03  
**Status:** Accepted

**Decision:** Unverified vendors are **not indexed** in public search.

**Rationale:** Islamic ecosystem positioning requires trust. Bikroy's weakness is noise.

---

## ADR-007: Bilingual

**Date:** 2026-07-03  
**Status:** Accepted

**Decision:** Bengali + English at launch. Arabic UI in expansion markets (Phase 3).

---

## ADR-008: Shariah Guardrails

**Date:** 2026-07-03  
**Status:** Accepted

**Decision:** No riba product listings. Sponsored content always labeled. Haram categories blocked. Shariah board before finance module.

**Rationale:** "Earn from the Ummah" must be ethical and transparent to win long-term trust.

---

## ADR-009: Ecosystem Marketing

**Date:** 2026-07-03  
**Status:** Accepted

**Decision:** Primary GTM = market **customer demand posts**, not app install ads.

**Rationale:** Solves chicken-and-egg. Vendors follow leads.

---

## ADR-010: Monorepo Location

**Date:** 2026-07-03  
**Status:** Accepted

**Decision:** Taqdimah lives in `founders-kit/Taqdimah/` until MVP traction; may split to own repo later.

---

**Related:** [PRD.md](./PRD.md) · [BUSINESS_PLAN.md](./BUSINESS_PLAN.md)