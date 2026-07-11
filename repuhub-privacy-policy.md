# RepuHub Privacy Policy — Google API / OAuth Data Disclosure (DRAFT)

> **Status:** First real draft — 2026-07-11. **Not yet published, not legal advice.**
> **Scope note (see README §3.5.6):** This is *not* the same document as `privacy.html` in this repo. That page covers the Mo'men Store brochure site (used only as the qualifying GBP business for the Basic API Access request in Phase 5). This document instead covers **RepuHub's own product** — what RepuHub's customers see and agree to on RepuHub's OAuth consent screen when they connect their Google Business Profile.
> **Where this needs to live:** Hosted on the same verified domain as RepuHub's OAuth consent screen home page — i.e. `repuhub.xyz` or `repuhub.ai` per the redirect URIs already configured in Phase 6.4 — **not** on `momenstore.com`.
> Every `[FILL IN: ...]` marker below needs a real answer from you before this is usable, and it needs a legal review before publishing (see closing note).

---

## 1. Overview

RepuHub ("RepuHub," "we," "our," or "us") is a multi-tenant SaaS platform that helps local businesses manage and respond to their Google reviews. This policy explains what happens when a business owner ("you," "your," or "the Customer") connects their Google account to RepuHub via Google OAuth 2.0, what data we access as a result, and how we handle it.

This policy applies specifically to data RepuHub accesses through Google APIs. It does not cover data you give us directly outside of Google (e.g. account signup details) — that belongs in RepuHub's general/product privacy policy, referenced from the same footer as this page. `[FILL IN: link to RepuHub's general privacy policy, if separate from this one, or confirm this document is the single combined policy]`.

## 2. Information We Access From Your Google Account

When you authorize RepuHub, you grant access to the `https://www.googleapis.com/auth/business.manage` scope. Through this, RepuHub accesses:

- **Business location information** — business name, address, phone number, categories, and hours for the Google Business Profile location(s) you authorize
- **Reviews** — the content, star rating, and reviewer-provided display name/photo (as supplied by Google) for reviews on your authorized location(s)
- **Owner responses** — the ability to read and post replies to reviews on your behalf, at your direction

RepuHub only requests this scope for business owners/managers who explicitly authorize it through Google's standard OAuth consent flow. We do not request or access consumer Google Account data (email, contacts, Drive, etc.) — only Business Profile management data covered by the scope above.

## 3. How We Use This Information

We use the data above solely to provide the features you see in the RepuHub dashboard:

- Displaying your business's reviews and ratings in one place
- Letting you draft and publish owner responses to reviews via the API
- Keeping your business location details in sync between Google and RepuHub

We do not use this data to build user profiles for advertising, sell it, or share it for any purpose beyond operating the features above.

## 4. Google API Limited Use Disclosure

RepuHub's use and transfer of information received from Google APIs adheres to the Google API Services User Data Policy, including the Limited Use requirements. Consistent with that policy:

- We do not use Google user data to serve advertising of any kind, including retargeted or personalized ads
- We do not sell or transfer Google user data to data brokers, information resellers, or other third parties for their own independent use
- We do not use Google user data to train generalized AI/ML models
- Human access to Google user data is limited to what's necessary for support, security, or legal compliance — not routine viewing

## 5. How We Store and Protect Data

Data accessed via the Google APIs described above is stored on `[FILL IN: hosting provider(s) / infrastructure — e.g. AWS region, GCP, etc.]`. We use `[FILL IN: relevant safeguards actually in place — e.g. encryption in transit via TLS, encryption at rest, access controls/role-based access, audit logging]` to protect it. `[FILL IN: any sub-processors with access to this data, if applicable]`.

## 6. Data Retention

We retain data accessed through your Google account for as long as your integration remains active, so the dashboard and review-response features can function. `[FILL IN: specific retention window after disconnection/account closure — e.g. deleted within 30 days]`. You can request earlier deletion at any time (see Section 8).

## 7. Sharing of Information

We do not sell your Google user data. We share it only:
- With sub-processors who help us run the service (e.g. hosting/infrastructure providers), under contractual terms consistent with this policy — `[FILL IN: name sub-processors if you want them listed explicitly, or keep this generic]`
- If required by law, or to investigate security incidents or abuse
- With your own team members within your RepuHub workspace, per your account's permission settings

## 8. Your Controls

You can revoke RepuHub's access to your Google account at any time from your [Google Account security settings](https://myaccount.google.com/permissions) or from within RepuHub's own integration settings. You can also request deletion of data RepuHub has synced from your Google account by contacting us (Section 12). Revoking access stops future syncing; it does not automatically delete data already synced — see Section 6 for retention.

## 9. Children's Privacy

RepuHub is a business-to-business product intended for business owners and staff. It is not directed at children, and we do not knowingly collect data from children through it.

## 10. Changes to This Policy

We'll update this page as RepuHub's use of Google APIs changes, and — consistent with Google's requirements — we will not begin a new use of previously-collected data without first updating this policy and, where required, prompting affected users for consent. "Last updated" date: 2026-07-11 (update this whenever the content changes).

## 11. Governing Law

`[FILL IN: governing law / jurisdiction for RepuHub as a company — this may differ from Mo'men Store's Jordan-law terms, depending on where RepuHub is legally incorporated]`.

## 12. Contact Us

Questions about this policy or RepuHub's use of your Google data:
📧 `[FILL IN: support/privacy contact email]`
🏢 `[FILL IN: RepuHub's legal entity name and registered address]`

---

> **Still outstanding before this is publishable (per README 3.5.6):**
> 1. Every `[FILL IN: ...]` marker above — legal entity name/address, hosting/sub-processors, retention window, support contact, governing law
> 2. Review by a licensed legal professional in whatever jurisdiction RepuHub is incorporated in (this draft is not legal advice and was not written by a lawyer)
> 3. Publish it on the same verified domain as RepuHub's OAuth consent screen home page (`repuhub.xyz` / `repuhub.ai` — not `momenstore.com`), then link it from both that home page and the OAuth consent screen config before submitting for verification (Phase 6.6)
