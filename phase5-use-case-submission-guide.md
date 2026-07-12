# Mo'men Store — GBP Basic API Access: Use Case & Submission Guide

**For:** Phase 5.3 (Use Case description) of the Google Business Profile API access request
**Target submission date:** July 20, 2026

---

## ⚠️ Read this before you paste anything in

The use case text below states the landing page is live at `momenstore.com`. As of July 12, that's not true yet — the domain hasn't been purchased, and the CNAME was just removed to stop the dead redirect. Two scenarios by July 20:

- **If momenstore.com is live and indexed by then** → use the text exactly as written below.
- **If it's still not live** → don't just swap in the `github.io` URL and submit anyway. Your own `README.md` (Section 2B) notes that Google Trust & Safety frequently rejects free-subdomain submissions outright — editing the sentence doesn't fix that, only finishing the domain migration does. If you're close to the 20th with no domain yet, it's worth pushing the submission date back a few days rather than submitting from a subdomain and risking a straight rejection.

---

## The Use Case Description (paste into Phase 5.3)

> Mo'men Store is a convenience store located on Ibrahim Bakr Street in Amman, Jordan, requesting Basic API Access to the Google Business Profile APIs to manage our own Google Business Profile listing directly. Once access is authorized through Google's standard OAuth 2.0 consent flow (scope: `https://www.googleapis.com/auth/business.manage`), it will be used to:
>
> - List and sync the reviews and star ratings on our own location's profile
> - Read and publish owner responses to those reviews
> - Keep our location details (name, address, phone, hours, categories) synced and up to date
>
> This is a single-location, first-party use case — access applies only to our own Business Profile, authorized directly by the business owner/manager through Google's OAuth consent screen, with no other businesses or third-party accounts involved. Our profile has been verified since May 20, 2026, and our landing page is live at momenstore.com with matching NAP data and Privacy Policy / Terms of Service pages already in place.

This is first-party for Mo'men Store only, no RepuHub framing — keep it that way when pasting.

---

## Submission steps — July 20

1. **Confirm the 60-day threshold has passed.** It crosses July 19; submitting on the 20th keeps the 1-day buffer already built into your timeline.
2. Go to the [GBP API Contact Form](https://docs.google.com/forms/d/e/1FAIpQLSe3sEsc6R-DNF24gPaINV6C6IFNvC5mGqF5WL7MxqJA5cYrMg/viewform).
3. Select **"Application for Basic API Access."**
4. Fill in business contact info — use `info@momenstore.com` if that mailbox exists by then; otherwise the GBP owner/manager's regular Google account email.
5. Enter your **Google Cloud Project Number** (not the Project ID) — copy it from the GCP Console dashboard (Phase 4.2).
6. Paste the Use Case Description above into the use-case field, adjusting the domain sentence per the warning at the top if needed.
7. **Double-check the email you're submitting with matches the GBP profile's owner/manager account** — this is one of the things Google checks.
8. Submit.
9. **Screenshot the confirmation page immediately.** Google doesn't reliably send a confirmation email, so this screenshot is your only record of submission.

---

## After you submit

- Check quota status every 2–3 days: **GCP Console → APIs & Services → Quotas**
  - `0 QPM` = still under review
  - `300 QPM` = approved
- If rejected, match the reason against the contingency table in `README.md` (Section 5) rather than guessing at a fix.

---

## Quick reference

| | |
|---|---|
| Business | Mo'men Store |
| Address | Ibrahim Bakr Street, Amman, Jordan |
| Phone | 07 9979 3446 |
| Verified since | May 20, 2026 |
| OAuth scope | `https://www.googleapis.com/auth/business.manage` |
| Target submission date | July 20, 2026 |