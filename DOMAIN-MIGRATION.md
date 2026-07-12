# Domain Migration Runbook (3.5.1 / Phase 2)

**Goal:** replace `https://yasir-alobaidi.github.io/momen/` with a real custom domain. This does **not** require leaving GitHub Pages as the host — GitHub Pages supports custom domains with free automatic HTTPS, which is the fastest path given the July 20 submission target.

Placeholder domain used throughout this repo's new files (`sitemap.xml`, `robots.txt`): `momenstore.com`. Find-and-replace it with whatever you actually buy. `CNAME` isn't part of that find-and-replace set — it's not in the repo yet; step 2 below has you create it fresh, for reasons explained there.

---

## 1. Buy a domain
- `momenstore.com` or `momenstore.jo` (both suggested in Section 2 of the README)
- `.jo` reads as more locally authentic but Jordanian registrars typically require more verification paperwork; `.com` is faster to get live through any standard registrar (Namecheap, Cloudflare Registrar, GoDaddy, etc.) if you're racing the clock

## 2. Point it at GitHub Pages
1. **Create** a `CNAME` file at the repo root containing just your real domain on a single line (e.g. `momenstore.com`) — it's intentionally not pre-built and included in this batch: a `CNAME` pointing at a domain whose DNS isn't configured yet makes GitHub Pages show a dead/broken redirect instead of your site, so it's created fresh only once you actually own the domain. Do that now, then continue with the DNS records below.
2. At your DNS provider, add:
   - **Apex domain** (`momenstore.com`) → four **A** records:
     `185.199.108.153` · `185.199.109.153` · `185.199.110.153` · `185.199.111.153`
   - **`www` subdomain** → one **CNAME** record → `yasir-alobaidi.github.io`
     (GitHub recommends configuring both even if you'll only advertise one publicly — it auto-redirects between them)
3. In the repo: **Settings → Pages → Custom domain**, enter your domain, wait for the DNS check to pass, then check **Enforce HTTPS**. Can take up to ~24h after DNS propagates.

*(Source: GitHub's current official custom-domain docs — worth re-confirming the IPs at [docs.github.com](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site) if you're reading this much later, since they *can* change.)*

## 3. Domain-matched email (`info@momenstore.com`)
GitHub Pages is static hosting only — it can't send or receive mail, so you need a separate service:
- **Free:** Cloudflare Email Routing or ImprovMX — forwards `info@momenstore.com` to an inbox you already have
- **Paid (~$6–7/mo):** Google Workspace — real Gmail-based inbox if you also want to *send* from that address, not just receive

## 4. Search Console + indexing
1. Add the new domain as a property in Google Search Console — DNS TXT record verification is the simplest method (one more record at your registrar)
2. Submit `sitemap.xml` (included in this batch — swap in your real domain first)
3. `robots.txt` (also included) already points at the sitemap
4. A few days later, search `site:momenstore.com` to confirm indexing — this is Section 2A's check, and also what 3.5.1 flagged as required before the OAuth consent screen's home page can be verified

## 5. Once the domain is actually live
- [ ] Add a `"url"` field to the JSON-LD block in `index.html` — it's already flagged with a TODO comment right above that block: `"url": "https://momenstore.com"`
- [ ] Update the GBP dashboard website link (Phase 3.1)
- [ ] Update README.md Section 3's "Website URI" row
- [ ] Re-run the `site:` indexing check

---

**Files in this batch that use the placeholder domain and need a find-and-replace before use:** `sitemap.xml`, `robots.txt`. (`CNAME` isn't in the batch — create it fresh per step 2 above once you own the domain, rather than find-and-replacing a placeholder version.)
