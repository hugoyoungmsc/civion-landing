# Civion landing page — `civion.cloud`

Static marketing site for Civion, the EC2 reinforced concrete section design tool.

No build step, no framework, no server. Plain HTML/CSS, served by GitHub Pages.

## Files

| File | Purpose |
|---|---|
| `index.html` | Landing page: hero, problem, how it works, report, examples, audience, early access |
| `styles.css` | All styling; brand colours from `HugoYoung/assets/brand.md` |
| `terms.html` | Terms of Service — simplified early-access policy (Civion + email; no legal name/address) |
| `privacy.html` | Privacy Policy — simplified early-access policy (Civion + email; no legal name/address) |
| `404.html` | GitHub Pages 404 |
| `CNAME` | `civion.cloud` — required by GitHub Pages |
| `robots.txt` | Allows indexing; points to the sitemap |
| `sitemap.xml` | Home, Terms, Privacy |
| `assets/civion-mark.svg` | Wordmark mark |
| `assets/favicon.svg` | Favicon |
| `assets/pm-hero.svg` | Hero P-M interaction diagram (from the EC2 §6.1 worked example) |
| `assets/og.png` | 1200 × 630 social preview |

## Before publishing — review checklist

- [ ] Read the landing page copy aloud; confirm every claim is true for the product **as it exists at publication** (it currently says “in development” and “early access”).
- [ ] Confirm the pricing wording: the page says **free during early access** and deliberately states no price. Paid-plan pricing is a later decision.
- [ ] Review the expert/verification disclaimer; it must stay.
- [ ] **Legal pages are deliberately simplified:** they identify **Civion** and `hugo@civion.cloud` only — no real name, no address, no governing-law clause. This is the founder’s decision. It is **not** a full legal-entity disclosure and may not satisfy data-protection or consumer-law requirements in every jurisdiction.
- [ ] Accept that risk for the free early-access phase. Before paid plans, Paddle, or a wider public launch, add a legal operator identity, address, governing law and refund policy, and get legal review.
- [ ] Decide the waitlist mechanism. The current CTAs use `mailto:hugo@civion.cloud` — they work with no service. For a proper form, create a Tally or Formspree form and replace the CTA blocks; then update `privacy.html` to name the provider.
- [ ] Check the mobile layout at 360–400 px and the desktop layout at 1440 px.
- [ ] Test every link and the email CTA.
- [ ] Check the social preview (OG image) in a card validator after deployment.
- [ ] Decide whether a cookie/analytics banner is needed. The site currently uses no cookies or analytics.

## Legal operator — the choice made

The legal pages now identify **Civion** and `hugo@civion.cloud` only. No real name, address or governing-law clause is published. This is a deliberate early-access simplification, not a full legal-entity disclosure.

What this means:
- A privacy policy normally identifies the controller (the legal person or company) and a contact address. The current pages identify only the brand and an email.
- For a free, email-only early-access page the practical risk is lower, but it is not zero. Some jurisdictions require a legal name and postal address for a website that collects personal data.
- **Before paid plans, Paddle, or a wider launch**, add the legal operator name/address/governing law and a refund policy. Paddle KYC will require the real identity privately even if the public page stays under the Civion brand.
- This is a legal decision, not a design one — get legal advice before relying on the simplified pages for a paid product.

## Deploy to GitHub Pages

1. Create a **public** repository under `hugoyoungmsc`, suggested name `civion-landing`.
2. From this folder:

   ```bash
   git init
   git add .
   git commit -m "Civion landing page"
   git branch -M main
   git remote add origin https://github.com/hugoyoungmsc/civion-landing.git
   git push -u origin main
   ```

3. In GitHub: **Settings → Pages → Deploy from a branch → `main` / root**.
4. Set **Custom domain** to `civion.cloud` (the `CNAME` file is already in the repo).
5. In **AliCloud DNS** for `civion.cloud`:

   **Current state, checked 28 October 2026:** `@` and `www` both point to **18.226.231.212** — the old AWS server, now suspended. Replace both records. The mail records are live and must stay:
   - MX: `mx1.qiye.aliyun.com` (5), `mx2.qiye.aliyun.com` (10), `mx3.qiye.aliyun.com` (15)
   - SPF TXT: `v=spf1 include:spf.qiye.aliyun.com -all`
   - Nameservers: `ns01.trs-dns.com` and the other AliCloud DNS servers

   Website records to set:
   - `@` → four **A** records: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `www` → **CNAME** to `hugoyoungmsc.github.io`

   The apex `civion.cloud` becomes the marketing page. When the Civion app is hosted again, put it on **`app.civion.cloud`** (a separate A/CNAME record to the app host) rather than pointing the apex back at a server.
6. Wait for the DNS check, then enable **Enforce HTTPS**.
7. Visit `https://civion.cloud` and `https://www.civion.cloud`; confirm both resolve and the certificate is valid.

**Do not change the MX, SPF or DKIM records.** They run `hugo@civion.cloud` email. Adding A/CNAME records for the website does not affect mail.

## Paddle prerequisites

The site is built to cover the website-review items identified in `HugoYoung/journal/2026-08-13-paddle-research.md`:

- product landing page with a clear description of the product;
- Terms of Service;
- Privacy Policy;
- contact (`hugo@civion.cloud`);

Before applying to Paddle, add a legal operator identity, pricing and a refund policy — the current pages are deliberately simplified and the beta is free. Paddle KYC will require the real identity privately. Get legal review before applying.

## Notes

- The P-M diagram is copied from the EC2 §6.1 worked example. If the example changes, replace `assets/pm-hero.svg`.
- The page uses system fonts and local assets only — no Google Fonts, no external scripts, no analytics.
- The page is intentionally separate from the Hugo Young blog (`hugoyoungmsc.github.io`). The blog is the engineering notebook; this is the product site.
- The legal pages are a simplified early-access policy (Civion + contact email), not a full legal-entity disclosure or legal advice.
