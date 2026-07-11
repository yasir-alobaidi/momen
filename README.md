# Google Business Profile & API Access Master Checklist

> **Last updated:** 2026-07-11  
> **Status:** ▶ In progress — 9 days until submission window opens

## 1. Timeline & 60-Day Milestone Check

| Milestone | Date |
|---|---|
| Official Verification Date | May 20, 2026 |
| Current Assessment Date | **July 11, 2026** |
| Total Days Active | **52 days** |
| 60-day threshold crossed | **July 19, 2026** |
| **Recommended submission date** | **July 20, 2026** (1-day buffer) |

> **Submission buffer:** Google's automated systems are strict about "60+ days active." A 1-day buffer prevents algorithmic rejection.

---

## 2. Website & Domain Compliance

### A. Landing Page Requirements
- **NAP Consistency:** Business Name (*Mo'men Store*), Address (*Ibrahim Bakr Street, Amman*), Phone (*07 9979 3446*) must match GBP character-for-character
- **HTTPS mandatory** — Google rejects HTTP-only applications immediately
- **Indexing check:** Search `site:yourdomain.com` on Google — page must be indexed before applying
- Professional appearance with clear value proposition

### B. Custom Domain (Mandatory)
- Google Trust & Safety frequently rejects free subdomains (`wixsite.com`, `github.io`)
- Must upgrade to a custom TLD (e.g., `momenstore.com`)
- Professional domain-based email recommended (e.g., `info@momenstore.com`)

---

## 3. Live Profile Integrity — Gap Analysis

| Field | Current Value | Status | Action |
|---|---|---|---|
| Business Name | `Mo'men Store` | ✅ | Match physical signage exactly |
| Primary Category | `Convenience Store` | ✅ | Specific category, good |
| Primary Phone | `07 9979 3446` | ✅ | Active local number |
| Storefront Address | Ibrahim Bakr Street, Amman, JO | ✅ | Tied to Place ID |
| Website URI | `https://yasir-alobaidi.github.io/momen/` | ⚠️ **Change** | Swap to custom HTTPS domain |
| Regular Hours | Split Schedule (Mon-Wed 8AM-12PM; Thu-Sun 9AM-5PM) | ✅ | Confirmed current 2026-07-11 (see 3.5.2); still verify against physical signage (1.1) |
| Business Description | Present | ✅ | 2-3 sentence overview |
| Attributes | Not fully mapped | ⚠️ **Gap** | Add accessibility, Wi-Fi, etc. |
| Visual Media | Needs review | ⚠️ **Gap** | Upload exterior, interior, product photos |
| Reviews & Engagement | Active status | ⚠️ **Gap** | Need 2-3 genuine reviews with owner responses |

---

## 3.5 Landing Page Audit — Action Items

> ⚠️ Added 2026-07-11 — findings from reviewing `index.html` / `privacy.html` against this checklist and current Google documentation (developers.google.com/my-business, developers.google.com/identity/protocols/oauth2). Content/design work is solid; gaps below are what's standing between this and submission.

### Blocking — do this first
- [ ] **3.5.1** Migrate off the GitHub Pages subdomain (duplicate of 2.1/2.2, elevated here because it's load-bearing for two separate things, not just "professional appearance"):
  - No domain-matched business email is possible on a `github.io` subdomain — Google's FAQ lists this as how you demonstrate legitimacy for Basic API Access
  - The OAuth consent screen (Phase 6.6) requires a home page on a domain you can verify ownership of via Search Console — shared subdomains don't qualify
  - ⚙️ **Prep done:** `DOMAIN-MIGRATION.md` (step-by-step runbook), `CNAME`, `sitemap.xml`, `robots.txt` in repo — all three files use `momenstore.com` as a placeholder. **Still needs you:** actually buying the domain (can't be done from here) — everything after that is copy-paste from the runbook.
  - 🛠️ **Fixed 2026-07-11:** the runbook's content had actually been saved under the wrong filename — it was sitting in `repuhub-privacy-policy.md`, colliding with the unrelated document 3.5.6 needs. `robots.txt` was also empty despite being listed as ready. Runbook content moved to `DOMAIN-MIGRATION.md` (its correct name, unchanged otherwise); `robots.txt` now actually contains the allow-all + sitemap rule the runbook describes. Flagging in case this same mix-up affected copies elsewhere.

### Content fixes — do before submitting
- [x] **3.5.2** Reconcile hours: confirmed 2026-07-11 that the split schedule (Mon-Wed 8AM–12PM; Thu-Sun 9AM–5PM) is what's actually current and matches the live GBP listing — the "every day 9:00 AM–10:00 PM" copy in `index.html` was the stale value. Updated the visible "Opening Hours" block and the JSON-LD `openingHoursSpecification` (now two entries, one per day-range) to match. Still worth a final check against the storefront hours plaque before submission (see 1.1).
- [x] **3.5.3** Confirm address string: updated `index.html` (JSON-LD `streetAddress`, Store Info block, map card, footer) and `privacy.html` (contact block) — all 5 instances now read "Ibrahim Bakr Street" to match the ✅-confirmed Section 3 value. Still worth a final character-for-character check against the live listing itself before submission.
- [x] **3.5.4** Complete footer NAP per 2.3: footer currently has business name + city only, no street address or phone. Full contact info exists in the "Store Information" section but isn't duplicated into the footer itself.
- [x] **3.5.5** Add a Terms of Service page per 2.4. Created `terms.html`, mirroring `privacy.html`'s design system exactly (same tokens/layout/structure). Covers acceptable use, IP, third-party links, accuracy-of-info, no-warranty/liability, Jordan governing law, and contact — with the same "not legal advice, have a Jordan-licensed professional review it" note. Cross-linked from the footer of all three pages.

### Decision needed — not resolved anywhere else in this doc
- [ ] **3.5.6** Decide what privacy policy backs RepuHub's *own* production OAuth consent screen. Phase 6.6 currently assumes reusing momenstore.com's `privacy.html`, but that policy is explicitly scoped to a brochure site with no forms/accounts — it says nothing about OAuth, reviews, or business-location data. The Basic API Access request (Phase 5) is fine using Mo'men Store as the qualifying GBP; Google explicitly allows the qualifying profile to be the applicant's own business rather than the product itself. But the consent screen RepuHub's *customers* see needs a privacy policy that actually discloses RepuHub's data practices, hosted on the same domain as whatever home page is linked from it. Given Phase 6.4's redirect URIs already point at `repuhub.xyz` / `repuhub.ai`, this likely means a separate RepuHub-branded privacy policy — not momenstore.com's — needs drafting before 6.6.
  - 🛠️ **Corrected 2026-07-11:** the file meant to hold this draft (`repuhub-privacy-policy.md`) actually contained the domain-migration runbook instead (see the fix noted under 3.5.1) — this decision was still fully open going into today, despite this item's sub-bullet previously implying a draft existed. A real first draft now lives at `repuhub-privacy-policy.md`, scoped to RepuHub's actual OAuth data access (reviews, business location, owner responses via `business.manage`) and including the Google-required Limited Use disclosure language. **Still needs you:** every `[FILL IN: ...]` marker in the doc (legal entity + address, hosting/sub-processors, retention window, support contact, governing law), a legal review, and publishing it on the same verified domain as RepuHub's OAuth consent-screen home page (`repuhub.xyz`/`repuhub.ai` — not `momenstore.com`).

---

## 4. Step-by-Step Readiness Checklist

### Phase 1: Physical Verification (Days 52–54 / by July 13)
- [ ] **1.1** Verify physical storefront hours plaque matches digital split hours
- [ ] **1.2** Confirm store sign reads exactly `Mo'men Store` (no variations)
- [ ] **1.3** Take timestamped photos of storefront showing sign + hours (useful if Google requests proof)

### Phase 2: Web Compliance & Custom Domain (Days 54–57 / by July 16)
- [ ] **2.1** Purchase custom domain (e.g., `momenstore.com` or `momenstore.jo`) — see `DOMAIN-MIGRATION.md` for the full runbook
- [ ] **2.2** Route landing page to custom domain with SSL (enforce HTTPS) — covered in `DOMAIN-MIGRATION.md` §2
- [x] **2.3** Add NAP data (exact business name, address, phone) in the landing page footer
- [x] **2.4** Add Privacy Policy and Terms of Service pages (even placeholder — required for OAuth consent screen) — both live: `privacy.html`, `terms.html`
- [ ] **2.5** Submit sitemap to Google Search Console for faster indexing — `sitemap.xml` + `robots.txt` ready in repo (placeholder domain); submission itself needs Search Console access once the domain is live
- [ ] **2.6** Validate indexing: `site:yourcustomdomain.com` returns results

### Phase 3: GBP Dashboard Updates (Days 57–58 / by July 17)
- [ ] **3.1** Swap website link on GBP dashboard from GitHub Pages → new custom domain
- [ ] **3.2** Add missing profile attributes (accessibility, parking, payment methods, Wi-Fi)
- [ ] **3.3** Upload high-quality photos: exterior (2-3), interior (2-3), products (3-5)
- [ ] **3.4** Ensure 2-3 genuine customer reviews exist with professional owner responses
- [ ] **3.5** Add business logo and cover photo if missing

### Phase 4: Google Cloud Environment (Days 58–59 / by July 18)
- [ ] **4.1** Log into GCP Console with the **Owner/Manager** Google account of the GBP
- [ ] **4.2** Create new project (e.g., `momen-store`) — copy **Project Number** from dashboard
- [ ] **4.3** Enable Google Cloud Billing (link valid payment method — required even for free tiers)
- [ ] **4.4** ⚠️ **Set up OAuth consent screen** (missing from original checklist):
  - Navigate to APIs & Services → OAuth consent screen
  - Choose "External" user type
  - Fill app name, support email, authorized domain (your custom domain)
  - Add scopes: `https://www.googleapis.com/auth/business.manage`
  - **Do NOT submit for verification yet** — just save as "Testing" for now
- [ ] **4.5** ⚠️ **Enable the required APIs in GCP Library** (do this BEFORE submitting the form):
  - My Business Account Management API
  - My Business Business Information API
  - Google My Business API (v4, for reviews)
  - My Business Notifications API

### Phase 5: Submit Access Request (Day 60+ / **July 20, 2026**)
- [ ] **5.1** Navigate to the official [GBP API Contact Form](https://docs.google.com/forms/d/e/1FAIpQLSe3sEsc6R-DNF24gPaINV6C6IFNvC5mGqF5WL7MxqJA5cYrMg/viewform)
- [ ] **5.2** Select **"Application for Basic API Access"**
- [ ] **5.3** Fill in:
  - Business contact information (use domain email if possible)
  - Google Cloud **Project Number** (not Project ID)
  - **Use Case description** — example: *"RepuHub is a multi-tenant SaaS platform that helps local businesses manage and respond to Google reviews. We need API access to: (1) list and sync Google Business Profile reviews for our customers, (2) post owner responses to reviews via the API, and (3) manage business location information. Our platform serves verified business owners who authorize access via standard OAuth 2.0."*
- [ ] **5.4** Verify submission email matches the GBP profile owner/manager account
- [ ] **5.5** ⚠️ **Screenshot the confirmation page** — Google doesn't always send a confirmation email

### Phase 6: Monitoring & Activation (Post-Submission)
- [ ] **6.1** Check quota status every 2-3 days:
  - GCP Console → APIs & Services → Quotas
  - `0 QPM` = Under review / Not approved
  - `300 QPM` = **Approved**
- [ ] **6.2** Once approved (300 QPM), manually enable in API Library:
  - Google Business Profile Business Information API
  - Account Management API
- [ ] **6.3** Generate production OAuth 2.0 Client ID credentials
- [ ] **6.4** ⚠️ **Configure authorized redirect URIs** in the OAuth credential:
  - Dev: `http://localhost:8000/api/v1/integrations/google/oauth/callback/`
  - Staging: `https://api.repuhub.xyz/api/v1/integrations/google/oauth/callback/`
  - Prod: `https://api.repuhub.ai/api/v1/integrations/google/oauth/callback/`
- [ ] **6.5** ⚠️ **Remove GBP mock env vars** from `deploy/.env.staging` once real credentials work (see `CLAUDE.md` §Removing the mock)
- [ ] **6.6** ⚠️ **Submit OAuth consent screen for verification** (required for production use beyond 100 users):
  - Requires privacy policy URL — draft now at `repuhub-privacy-policy.md`, see **3.5.6** for what's still outstanding before it's publishable
  - Verification can take 4-6 weeks — submit early

---

## 5. Contingency: If Application is Rejected

> ⚠️ Missing from original checklist — added 2026-07-11

| Rejection reason | Resolution |
|---|---|
| "Business not verified long enough" | Wait additional 30 days, reapply |
| "Website doesn't match" | Fix NAP data alignment, wait for re-indexing, reapply |
| "Use case unclear" | Rewrite description with more specifics about review management |
| "Free subdomain" | Migrate to custom domain (see Phase 2) |
| Generic / unclear | Submit appeal via [GBP API support form](https://support.google.com/business/gethelp), reference your Project Number |
| **Alternative if delayed:** | Continue using GBP mock on staging; launch US market with mock; swap to real API once approved. No user-facing impact since GBP integration works identically. |

---

## 6. Post-Approval Checklist (NEW)

> ⚠️ Missing from original checklist — added 2026-07-11

- [ ] Test real Google OAuth flow end-to-end on staging
- [ ] Verify `accounts.list`, `locations.list`, `reviews.list` all return real data
- [ ] Test posting a reply to a real review (on a test/low-risk review)
- [ ] Compare real API response shapes vs. GBP mock — fix any mismatches
- [ ] Monitor quota usage for first 24 hours (stay well under 300 QPM)
- [ ] Set up Google Cloud Monitoring alerts for quota approaching limits
- [ ] Document the real vs. mock differences (if any) in `CLAUDE.md`