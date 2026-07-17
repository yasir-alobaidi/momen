# Mo'men Store — OAuth Consent Screen (Google Auth Platform) Setup Guide

**For:** Phase 4.4 of the master checklist — branding, audience, and scope justification for the `momen-store` GCP project
**Do before:** Phase 5 submission (July 20) — this shares the same domain dependency as that phase

---

## One naming heads-up before you start

Google renamed "OAuth consent screen" to **Google Auth Platform** in 2024. It's the same thing your README already describes, just relocated: **APIs & Services → Google Auth Platform**, split into four tabs — Branding, Audience, Data Access, Clients. If the old menu item isn't there when you go looking, that's why — not a permissions problem.

---

## ✅ Domain dependency cleared

`momenstore.com` is live — the home page and authorized domain fields below can be filled in as-is now. (Still add/verify the domain in Search Console per `DOMAIN-MIGRATION.md` §4 before submitting the consent screen, since Google checks ownership verification.)

## Branding tab — paste-ready values

| Field | Value |
|---|---|
| App name | Mo'men Store Business Profile Manager |
| User support email | `info@momenstore.com` once that mailbox exists, otherwise the GBP owner/manager's own Google account email |
| Application home page | `https://momenstore.com` *(blocked until domain is live)* |
| Privacy policy link | `https://momenstore.com/privacy.html` |
| Terms of service link | `https://momenstore.com/terms.html` |
| Authorized domain | `momenstore.com` *(needs Search Console verification first)* |

## Audience tab

- Choose **External.** Internal requires the account to be part of a Google Workspace organization — a single-owner Google account isn't, so External is the only real option here even though only one person will ever use this.
- **Add yourself as a test user.** Not in the original checklist, but required: External apps in Testing mode block sign-in for anyone not on the Test users list — including you, the app's only intended user. Skip this and you'll hit an `access_blocked` error the first time you try to authorize it.

## Data Access tab

1. **Add or Remove Scopes** → make sure the Business Profile APIs are enabled first (Phase 4.5), then add:
   `https://www.googleapis.com/auth/business.manage`
2. If a justification field appears for this scope (Google requires one for sensitive/restricted scopes — may show up here or later at verification), paste:

   > Mo'men Store Business Profile Manager uses the `business.manage` scope so the store's own owner/manager account can list and sync reviews and star ratings on our Google Business Profile listing, read and publish owner responses to those reviews, and keep our location details (name, address, phone, hours, categories) synced and up to date. This is a single-location, first-party integration — the account authorizing access is the same account that owns the profile being managed, and no other business's data is ever accessed. `business.manage` is the only Business Profile scope covering both review management and location-detail sync, which are both core to what the tool does, so a narrower scope isn't sufficient.

## Stop at "Testing" — don't publish yet

Matches what your README already says: save this as Testing, don't click "Publish app" or submit for verification. Move on to Phase 4.5 (enabling the APIs) and then Phase 5.

---

## Where this leaves the "draft now while we wait" list

- ✅ Use Case description (Phase 5.3) — done
- ✅ OAuth consent screen branding + scope justification (Phase 4.4) — done, this file
- ✅ Attributes checklist (Phase 3.2) — already sitting in your repo as `attributes-checklist.md`

Everything that can be prepared without touching a live dashboard is now ready to paste in when you get there. What's left is genuinely gated on the domain purchase and on you being logged into the actual GBP/GCP accounts.

## Quick reference

| | |
|---|---|
| GCP project | `momen-store` (Phase 4.2) |
| Scope | `https://www.googleapis.com/auth/business.manage` |
| Authorized domain | `momenstore.com` (pending purchase) |
| User type | External, Testing mode |