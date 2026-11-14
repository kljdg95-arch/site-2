# CUDER website (v4)

Static site for GitHub Pages (domain: `cuder.ir`, see `CNAME`). No build step: upload the folder as-is.

## Structure
- `index.html`, `projects.html`, `labs.html`, `discover.html`, `resources.html`, `roadmap.html`, `changelog.html`, `about.html`, `contact.html`, `support.html`, `faq.html`, `legal.html`, `account.html`, `reviews.html`, `search.html`, `404.html`: thin HTML shells (per-page title, description, canonical, Open Graph and a readable fallback `<h1>` + links). The real UI is rendered by JS.
- `bizflow/`, `downflow/`: each product has overview, features, pricing, download pages and its own installable web app in `app/` (independent data, logic and service worker).
- `js/config.js`: **site settings.** Set `api` to your backend URL to switch on real sign-up/sign-in and the contact form. While `api` is empty, the site says honestly that public accounts are not active and the contact form opens the visitor's email app.
- `js/data.js`: **all content** (projects, articles, guides, roadmap, changelog, legal text) and the global search function. Add a project/article here and it appears in lists, search and the Ctrl/⌘+K palette.
- `js/pages-extra.js`: UI for the new pages. `js/site-*.js`: page content for each site. `js/core.js`: shared engine (header, footer, language, theme, effects, palette).
- `css/base.css`: design system (tokens `--c1…--c6`, glass cards, aurora, motion). `prefers-reduced-motion` is respected.
- `sitemap.xml`, `robots.txt`: update `lastmod` when pages change.

## Product apps (real, client-side features)
- **BizFlow** `bizflow/app`: new "تحلیل" tab: profitability (product/customer), reorder suggestions, 8-week cash-flow forecast, customer segments, monthly budgets, audit trail (stored on the device).
- **DownFlow** `downflow/app`: new "ابزارها" menu (`extras.js`): usage stats, live speed chart, link inspector & diagnostics, mirror speed test with automatic failover, network profiles / metered hint, filename templates, smart folders, content-hash duplicate detection. Engine changes are in `webshim.js`.
- Each product also has Docs, Changelog and FAQ pages (`js/product-extra.js`, content in `js/data.js`).

## Security
Every page has a Content-Security-Policy meta tag (scripts only from this site, cdnjs and jsDelivr for optional Lottie/Rive). Add real HTTP headers (e.g. via Cloudflare) if you move off GitHub Pages.

## Publishing
Upload everything to the GitHub Pages repo root. `404.html` is used automatically.

## Needs infrastructure (not faked)
Accounts/sync, real contact form delivery, shared public reviews, and all server-dependent roadmap items. They are listed as "Planned" on the Roadmap page.

## Not possible without infrastructure
Multi-branch, approval workflows, customer portal, appointments, multi-currency sync, cloud storage targets, LAN transfer, archive extraction and background downloads need a backend or a desktop app. They are listed as Planned on the Roadmap.

## To confirm before launch
Email `info@cuder.ir` and the social handles in `js/config.js`; `assets/og.png` is a generated share image (replace it with your own if you prefer); legal texts need legal review.
