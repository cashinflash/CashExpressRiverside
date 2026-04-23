# Cash Express Riverside

Marketing website for **cashexpressriverside.com** — a Riverside-targeted ghost
site feeding the shared Cash in Flash apply pipeline.

- Legal entity: **Dhan Corporation** (Cash Express Riverside is a marketing dba).
- Source-attribution slug: `cashexpress_riverside` (stored in sessionStorage
  by apply.cashinflash.com and persisted on the backend as `source_site`).
- Deploy target: **Netlify** (static, no build step).
- Pre-launch embargo: `robots.txt` is `Disallow: /` — counsel must sign off
  before indexing is enabled.

## Placeholders (resolve before launch)
| Token | What to fill in |
|---|---|
| `[[LICENSE_NUMBER]]` | CDFPI deferred-deposit license # (usually `10DFPI-NNNNNN`) |
| `[[NMLS_ID]]` | NMLS consumer access ID |
| `[[YEAR_FOUNDED]]` | Copyright year (e.g. `2026`) |
| `[[CONTACT_EMAIL]]` | Customer / legal-notices email |
| `[[CONTACT_PHONE]]` | Toll-free support number |
| `[[GA4_ID]]` | New Google Analytics 4 property id |

A find-and-replace across the repo will resolve them. Run
`grep -r '\[\[' --exclude-dir=node_modules --exclude-dir=.git` to list remaining tokens.

## Apply CTAs
Every Apply button points at:
```
https://apply.cashinflash.com/?source_site=cashexpress_riverside&utm_source=cashexpressriverside.com&utm_medium=referral&utm_campaign=payday_riverside
```
This works without JavaScript — hrefs are hard-coded.

## Layout
```
/
├── index.html                  # Riverside payday-loan landing
├── rates-and-fees/index.html   # CA CFL §23035 disclosure
├── terms/ privacy/ security/   # rebranded legal (Dhan preserved)
├── css/style.css               # navy/gold palette
├── js/main.js, js/analytics.js # menu + GA loader (GA ID placeholder)
├── images/logo.svg             # inline SVG wordmark
├── fonts/poppins-*.woff2       # reused from cif-website
├── 404.html, robots.txt, sitemap.xml, site.webmanifest
├── netlify.toml                # security headers + caching
└── SOURCE_SITE                 # literal slug: cashexpress_riverside
```

## Local preview
```bash
python3 -m http.server 8000
```
Then open http://localhost:8000/.
