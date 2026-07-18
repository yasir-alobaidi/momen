# Mo'men Store — GBP Basic API Access: Use Case & Submission Guide

**For:** Phase 5.3 (Use Case description) of the Google Business Profile API access request
**Target submission date:** July 20, 2026

---

## ✅ Domain is live — use the text as written

`momenstore.com` is confirmed live and HTTPS. Use the use-case text below as-is. (Search Console indexing is still catching up — that doesn't block submission, Google's review doesn't require the site be indexed, just live and matching NAP.)

---

## Before you start — have these ready

Gather all of this *before* opening the form, so you're not stopping mid-submission to go find something:

- [ ] **Google Cloud Project Number** for `momen-store` (not the Project ID — copy from GCP Console → Dashboard → Project info card)
- [ ] **Confirmation you're the GBP Owner, not a Manager** — check this at [business.google.com](https://business.google.com) → your listing → **Users** (or "Business Profile settings → People and access"). Your own name should show the role **Primary Owner** or **Owner**, not "Manager." If it says Manager, whoever *is* the Owner needs to be the one signed in when the form is filled out.
- [ ] The Owner's actual Google Account email (the one from the check above) — some fields need to match this exactly
- [ ] All 4 required APIs confirmed enabled in GCP Library (Phase 4.5)
- [ ] The use-case text below, copied and ready to paste as-is

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
2. **Confirm you're signed in as the GBP Owner, not a Manager** (see the pre-flight check above). Google's API team reportedly bounces submissions made from a manager-level account — this isn't documented anywhere official, it's a known pattern from people who've been through the process, but it's a free thing to double-check.
3. Go to the [GBP API Contact Form](https://support.google.com/business/contact/api_default).
4. Select **"Application for Basic API Access."**
5. Fill in business contact info — use `contact@momenstore.com` as the general business contact, and the Owner's actual Google Account email anywhere the form asks for the account that will authenticate/own the request.
6. Enter your **Google Cloud Project Number** (not the Project ID).
7. Paste the Use Case Description above into the use-case field, exactly as written — no adjustment needed, it's already accurate to the current state of the site and profile.
8. **Double-check the email you're submitting with matches the GBP profile's Owner account** — this is one of the things Google checks.
9. Submit.
10. **Screenshot the confirmation page immediately.** Google doesn't reliably send a confirmation email, so this screenshot is your only record of submission.

---

## After you submit

- Google's own guidance says **up to 2 weeks** to process; real-world reports range from a few days to several weeks, so don't be alarmed if it's quiet for a bit.
- If you get a confirmation email, it usually includes a case number — save it, it's your reference for any follow-up.
- Check quota status every 2–3 days: **GCP Console → APIs & Services → Quotas**
  - `0 QPM` = still under review
  - `300 QPM` = approved
- If it's been **3+ weeks with no word**, follow up via the same [contact form](https://support.google.com/business/contact/api_default) or the [GBP API support form](https://support.google.com/business/gethelp), referencing your Project Number and case number if you have one.
- If rejected, match the reason against the contingency table in `README.md` (Section 5) rather than guessing at a fix.

---

## Quick reference

| | |
|---|---|
| Business | Mo'men Store |
| Address | Ibrahim Bakr Street, Amman, Jordan |
| Phone | 07 9979 3446 |
| Business contact email | contact@momenstore.com |
| GCP Project | `momen-store` |
| GCP Project Number | *(fill in from GCP Console → Dashboard before submitting)* |
| GBP Owner's Google Account email | *(fill in — confirmed via the pre-flight check above)* |
| Verified since | May 20, 2026 |
| OAuth scope | `https://www.googleapis.com/auth/business.manage` |
| Target submission date | July 20, 2026 |