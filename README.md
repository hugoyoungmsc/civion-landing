# Civion landing page — `civion.cloud`

Static marketing site for Civion, the EC2 reinforced concrete section design tool.

Plain HTML/CSS — no build step, no framework, no server. Served by GitHub Pages.

## Files

| File | Purpose |
|---|---|
| `index.html` | Landing page: hero, problem, how it works, report, examples, audience, early access |
| `styles.css` | All styling |
| `terms.html` | Terms of Service — simplified early-access policy |
| `privacy.html` | Privacy Policy — simplified early-access policy |
| `404.html` | 404 page |
| `CNAME` | `civion.cloud` — GitHub Pages custom domain |
| `.nojekyll` | Serve the static files without Jekyll processing |
| `robots.txt` | Allows indexing; points to the sitemap |
| `sitemap.xml` | Home, Terms, Privacy |
| `assets/civion-mark.svg` | Wordmark mark |
| `assets/favicon.svg` | Favicon |
| `assets/pm-hero.svg` | Hero P-M interaction diagram (from the EC2 §6.1 worked example) |
| `assets/og.png` | 1200 × 630 social preview |

## Local preview

Open `index.html` directly, or serve the folder:

```bash
python -m http.server 8000
```

## Notes

- System fonts and local assets only — no external scripts, no analytics, no cookies.
- The P-M diagram comes from the EC2 §6.1 worked example. If the example changes, replace `assets/pm-hero.svg`.
- The site is separate from the Hugo Young blog (`hugoyoungmsc.github.io`): the blog is the engineering notebook, this is the product site.

## Contact

hugo@civion.cloud
