# SpotON Supplies — Website Rebuild

Modern, static rebuild of https://www.spotonsupplies.co.za/ (originally a Wix site).
No frameworks or build step — plain HTML/CSS/JS. Host it anywhere (Netlify, Vercel,
Cloudflare Pages, cPanel, GitHub Pages).

**Repo:** https://github.com/itsyaku/spoton-supplies-website

## Deployment (Vercel)

The repo is configured for Vercel (`vercel.json` enables clean URLs). To deploy:

1. Go to https://vercel.com/new and sign in with GitHub (account `itsyaku`).
2. Install/authorize the Vercel GitHub App for the `spoton-supplies-website` repo.
3. **Import** the repo. Leave all build settings at their defaults — it's a static
   site: Framework Preset **Other**, no build command, output directory blank,
   root directory `./`.
4. Click **Deploy**. You get a `*.vercel.app` URL in ~30 seconds.

After the first import, **every `git push` to `main` auto-deploys**. To use the real
domain, add `spotonsupplies.co.za` under the project's Settings → Domains and update
the DNS records Vercel shows.

## Pages

| File | Purpose |
|---|---|
| `index.html` | Home — hero, stats, supply categories, about & apparel previews, client logos, CTA |
| `about.html` | Story, mission, values |
| `services.html` | Full supply range, who we serve, how ordering works |
| `apparel-branding.html` | Workwear, branding, display solutions, consulting + online collections |
| `catalogues.html` | All 9 catalogues (PDF downloads + online viewers) |
| `team.html` | Team directory with direct phone/WhatsApp/email |
| `contact.html` | Contact info, enquiry form, Google Maps embed |
| `clearance.html` | Priced clearance sale — 71 real products (46 glassware, 25 crockery) with filter tabs and per-item WhatsApp/email enquiry |

## Structure

- `css/styles.css` — single design-system stylesheet (brand colours from the logo: navy `#2e2a6d`, teal `#3d9583`)
- `js/main.js` — mobile nav, sticky header, scroll-reveal animations, stat counters, contact form handler
- `assets/` — logo, photography and client logos (downloaded from the current Wix CDN)

## Local preview

The `.claude/launch.json` config serves the site at http://localhost:8765 via
`powershell .claude/serve.ps1` (no Node/Python required).

## Important notes

- **Catalogue PDFs & company profile** still link to the live Wix URLs
  (`spotonsupplies.co.za/_files/...`). Before switching the domain to the new site,
  download those PDFs and host them locally (e.g. in an `assets/pdf/` folder), then
  update the links in `catalogues.html`, `contact.html` and `index.html`.
- **Contact form** opens the visitor's email app pre-filled (no backend needed).
  For a true in-page submit, connect a form service such as Formspree or Basin —
  one attribute change on the `<form>` tag.
- **Clearance sale banner** is the teal bar at the top of every page — edit or
  remove it in each HTML file (search for `class="announce"`).
- **Clearance products & prices** live in `js/clearance-data.js`. All names, codes,
  prices (ea ex VAT), pack sizes and quantities were transcribed from the live site's
  product images on 2026-07-10 — edit that one file to update or remove items.
- **WhatsApp** — the floating button and clearance enquiries use Schanel's number
  (+27 68 397 1914, general enquiries). Team cards use each member's own number.
  Confirm these numbers are on WhatsApp Business; change in `clearance.html`
  (`WA_NUMBER`), the `wa-float` link in each page, and `team.html`.
