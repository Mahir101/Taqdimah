# Taqdimah : Implementation Task Queue

> Agents: pick the first `pending` task, implement, update PROGRESS.md, mark task done.

---

## ALD-001 : Project Scaffold

**Phase:** Month 1  
**Priority:** P0  
**Status:** pending

**Description:** Initialize Next.js 15 app in `Taqdimah/` with TypeScript, Tailwind, ESLint, App Router, src directory.

**Acceptance criteria:**
- [ ] `npm run dev` works
- [ ] `npm run build` passes
- [ ] shadcn/ui initialized
- [ ] Landing page with Taqdimah branding + search input placeholder
- [ ] Environment variable template `.env.example`

**Commands:**
```bash
cd founders-kit/Taqdimah
npx create-next-app@latest . --typescript --tailwind --eslint --app --src-dir --import-alias "@/*"
npx shadcn@latest init
npm install @supabase/supabase-js @supabase/ssr
```

**References:** ARCHITECTURE.md §4

---

## ALD-002 : Database Schema

**Phase:** Month 1  
**Priority:** P0  
**Status:** pending  
**Depends on:** ALD-001

**Description:** Create Supabase migration with all MVP tables from SPECIFICATIONS.md.

**Acceptance criteria:**
- [ ] `supabase/migrations/001_initial.sql` applied
- [ ] RLS policies for profiles, vendor_profiles, leads, reviews
- [ ] Indexes for search and trust_score

**References:** SPECIFICATIONS.md §3

---

## ALD-003 : Category Seed Data

**Phase:** Month 1  
**Priority:** P0  
**Status:** pending  
**Depends on:** ALD-002

**Description:** Seed 50+ categories in Bengali + English including Islamic Ecosystem branch.

**Acceptance criteria:**
- [ ] `supabase/seed/categories.sql` or TS seed script
- [ ] Parent/child hierarchy correct
- [ ] Slugs URL-safe

**References:** PRD.md §9

---

## ALD-004 : Authentication

**Phase:** Month 1  
**Priority:** P0  
**Status:** pending  
**Depends on:** ALD-002

**Description:** Phone OTP + Google auth. Roles: user, vendor, admin.

**Acceptance criteria:**
- [ ] `/login`, `/register`, `/register/vendor`
- [ ] Vendor registration sets role + creates draft vendor_profile
- [ ] Middleware protects `/vendor/*` and `/admin/*`

---

## ALD-005 : Search API + UI

**Phase:** Month 1–2  
**Priority:** P0  
**Status:** pending  
**Depends on:** ALD-003, ALD-004

**Description:** Rule-based intent parser + PostgreSQL FTS search + results page.

**Acceptance criteria:**
- [ ] `GET /api/search` per SPECIFICATIONS.md
- [ ] `/search` results UI with vendor cards
- [ ] Trust score + verification badges displayed
- [ ] search_logs table populated

**References:** SPECIFICATIONS.md §4.1, §5

---

## ALD-006 : Vendor Public Profile

**Phase:** Month 2  
**Priority:** P0  
**Status:** pending  
**Depends on:** ALD-004

**Description:** Public profile page `/v/[slug]` with reviews, CTA, SEO meta.

**Acceptance criteria:**
- [ ] All fields from FEATURES.md F-004
- [ ] JSON-LD LocalBusiness schema
- [ ] "Request quote" button

---

## ALD-007 : Lead Request Flow

**Phase:** Month 2  
**Priority:** P0  
**Status:** pending  
**Depends on:** ALD-006

**Description:** User submits lead → vendor notified → vendor responds.

**Acceptance criteria:**
- [ ] `POST /api/leads`
- [ ] Rate limit 5/day per user
- [ ] Email notification to vendor
- [ ] User dashboard `/dashboard` shows lead status

**References:** FEATURES.md F-007

---

## ALD-008 : Vendor Dashboard

**Phase:** Month 2  
**Priority:** P0  
**Status:** pending  
**Depends on:** ALD-007

**Description:** Vendor hub: profile edit, lead inbox, respond/close.

**Acceptance criteria:**
- [ ] `/vendor` overview stats
- [ ] `/vendor/leads` inbox
- [ ] `/vendor/profile` edit form
- [ ] Response rate tracked for trust score

**References:** FEATURES.md F-008

---

## ALD-009 : Verification Workflow

**Phase:** Month 3  
**Priority:** P0  
**Status:** pending  
**Depends on:** ALD-008

**Description:** Document upload + admin approval queue.

**Acceptance criteria:**
- [ ] Vendor submits docs → status pending
- [ ] Admin approves → verification_level set → search indexed
- [ ] Rejected vendors get reason + resubmit

**References:** FEATURES.md F-005

---

## ALD-010 : Reviews & Trust Score

**Phase:** Month 3  
**Priority:** P0  
**Status:** pending  
**Depends on:** ALD-007

**Description:** Post-lead reviews + trust score computation job.

**Acceptance criteria:**
- [ ] Review only after lead closed
- [ ] trust_score recalculated on events
- [ ] Search ranking uses trust_score

**References:** FEATURES.md F-006, F-009; SPECIFICATIONS.md §6

---

## ALD-011 : Admin Console

**Phase:** Month 3  
**Priority:** P0  
**Status:** pending  
**Depends on:** ALD-009

**Description:** Moderation, verification queue, featured slot management.

**Acceptance criteria:**
- [ ] `/admin` role-protected
- [ ] Approve/reject vendors
- [ ] Audit log
- [ ] CSV bulk vendor import

**References:** FEATURES.md F-010

---

## ALD-012 : SEO City + Category Pages

**Phase:** Month 4  
**Priority:** P0  
**Status:** pending  
**Depends on:** ALD-005

**Description:** SSG pages for `/[city]/[category]` and sitemap.

**Acceptance criteria:**
- [ ] Dhaka, Chattogram, Sylhet city hubs
- [ ] Top 20 categories per city
- [ ] sitemap.xml auto-generated
- [ ] Bengali + English meta tags

**References:** FEATURES.md F-012

---

## ALD-013 : Premium Plans (Stripe/SSLCommerz stub)

**Phase:** Month 5  
**Priority:** P1  
**Status:** pending  
**Depends on:** ALD-008

**Description:** Pricing page + plan field on vendor_profiles. Payment integration can be manual first.

**Acceptance criteria:**
- [ ] `/vendor/upgrade` pricing table
- [ ] Plan stored on vendor_profiles.plan
- [ ] Pro badge on profile

**References:** BUSINESS_PLAN.md §4.2 Stream 1

---

## ALD-014 : Featured Listings

**Phase:** Month 5  
**Priority:** P1  
**Status:** pending  
**Depends on:** ALD-011

**Description:** Admin schedules featured_slots; search injects featured vendors.

**Acceptance criteria:**
- [ ] Max 3 featured per category+city
- [ ] Labeled "Featured" in UI
- [ ] featured_slots table used

**References:** BUSINESS_PLAN.md §4.2 Stream 2

---

## Dawah & Islah Tasks (Gift to the Khalifah)

These are critical to the reframed mission.

### DAW-001 : Islamic Ecosystem Category Expansion + Scholar Profiles

**Phase:** Month 1–2  
**Priority:** P0  
**Status:** pending

**Description:** Seed richer Islamic categories (Quran, scholars/da'ees, family counseling, revert support, dawah). Add distinct high-trust profile fields for L4 scholars.

### DAW-002 : Masjid Profile + Needs Board MVP

**Phase:** Month 3  
**Priority:** P1  
**Status:** pending

**Description:** Institution profiles for mosques with events, prayer info, and ability to post "needs" that route to verified participants.

### DAW-003 : Content Hub Foundation (Articles / Audio by verified contributors)

**Phase:** Month 4  
**Priority:** P1  
**Status:** pending

**Description:** Basic CMS or simple upload + listing for scholar-contributed beneficial knowledge. Tagging for topics.

### DAW-004 : Revert / New Muslim Support Flow

**Phase:** Month 5  
**Priority:** P2  
**Status:** pending

**Description:** Special matching to verified mentors + starter resources + masjid introduction.

### DAW-005 : "Ask Scholar" Lead Type + Public Q&A Seed

**Phase:** Month 5–6  
**Priority:** P2  
**Status:** pending

**Description:** New lead category for religious questions. Option to publish anonymized good answers into a knowledge base.

**Note:** All dawah features must have strong verification, adab guidelines, and disclaimers. Scholar review process required for L4 content.