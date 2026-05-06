# inknironapps-legal

Static creator-hub site → `inknironapps.com` (CNAME → GH Pages, repo name retains "legal" for history).

Two brands, one site:
- **Riley E. Antrobus** — author identity (books, author email, Facebook)
- **Ink & Iron Apps** — software brand (apps, workshop email `info@inknironapps.com`)

## Page tree

```
/                                                          → home (hero, books, apps, about)
/books/                                                    → all-books index
/books/warborn-protocols/                                  → series landing
/books/warborn-protocols/fleet-school-dropout.html         → book detail
/books/weaving-eternal-tapestry.html                       → standalone book detail
/apps/                                                     → all-apps index
/apps/libraryiq.html                                       → app detail
/apps/matcalc.html                                         → app detail
/apps/simmer.html                                          → app detail
/privacy-policy.html                                       → legal (used by app store listings)
/terms.html                                                → legal (used by app store listings)
/sitemap.xml · /robots.txt                                 → SEO
```

URL patterns:
- Books: `/books/<series-slug>/<book-slug>.html` for series, `/books/<book-slug>.html` for standalone. Don't shorten slugs → SEO match titles. New book in existing series → drop in series folder. New series → new folder under `/books/`.
- Apps: `/apps/<app-slug>.html` flat. No series concept. Icons live `/images/apps/<app-slug>.png` (square 512+ source).

App copy must match official Play Store listings exactly (taglines, feature lists, pricing). Pull from each app repo's `store-assets/store-listing.txt` or equivalent. Don't paraphrase — Safe Browsing classifiers flag mismatched promises.

Apps in alpha → mark "Closed alpha" in meta + body. CTAs = `mailto:info@inknironapps.com?subject=<app>%20alpha%20tester`. NO fake Play Store links until app actually published.

## Branch strategy (overrides global)

Push direct `main`. No `claude/dev`. No CI gate. Pages deploys main on push.

## Design system

Visual basis = `D:/Coding/inkironapps/brand/landing.html`. Palette/type/monogram/hero/sections lifted from there. No invent styling.

Web assets copied from `D:/Coding/inkironapps/brand/web/` + `D:/Coding/inkironapps/brand/` → repo root: favicons, OG image, manifest, `icon.svg`, `logo.svg`.

## SEO scaffolding (in place — keep parity on new pages)

Every page must have:
- `<link rel="canonical" href="https://inknironapps.com/...">`
- `<meta name="author">` + `keywords`
- OG: `og:url`, `og:site_name`, `og:locale`, `og:image` (absolute), `og:image:width/height`
- Twitter card full set
- JSON-LD blocks:
  - Home → `Person` (Riley) + `WebSite` + `Organization` (Ink & Iron Apps)
  - `/books/` → `CollectionPage` + `BreadcrumbList`
  - Series page → `BookSeries` + `BreadcrumbList`
  - Book detail → `Book` (with `workExample` per edition, ASIN as isbn) + `BreadcrumbList`
  - `/apps/` → `CollectionPage` (hasPart = `SoftwareApplication[]`) + `BreadcrumbList`
  - App detail → `SoftwareApplication` (operatingSystem, applicationCategory, publisher, author) + `BreadcrumbList`
  - Legal → canonical only

New page → register in `sitemap.xml`. Update `lastmod` on changed pages.

## Contacts on site

- Workshop / brand → `info@inknironapps.com` (footers everywhere)
- Author direct → `rileye.antrobus@gmail.com` (About section + book detail author-contact card)
- Author Facebook → `https://www.facebook.com/people/Riley-E-Antrobus/61580037872318/` (footers + About + book pages)

## Footer pattern (every page)

```
Ink & Iron Apps · inknironapps.com · info@inknironapps.com · Facebook
Privacy · Terms · © 2026
```

## Domain

CNAME = `inknironapps.com`. Don't replace with apex/www variant unless DNS confirmed.

Brand-name domain `inkniron.com` is **taken** (active Ink-N-Iron landing). "Apps" suffix on current domain disambiguates from established Ink-N-Iron festival/magazine/tattoo cluster — keep it.

## Email plan (NOT YET PROVISIONED — hold)

Currently single mailbox: `info@inknironapps.com`. Author uses `rileye.antrobus@gmail.com` directly.

When ready to expand, set up these as **aliases** (not separate mailboxes) all forwarding → one inbox. Free with Workspace/Fastmail/Zoho/Cloudflare email routing.

```
info@inknironapps.com      → primary  (general / workshop, current footers)
support@inknironapps.com   → primary  (app user issues — Play Store + App Store want this)
privacy@inknironapps.com   → primary  (privacy policy contact, GDPR/CCPA)
riley@inknironapps.com     → primary  (replaces rileye.antrobus@gmail.com on site)
noreply@inknironapps.com   → app outbound only (transactional sends)
```

Skip `legal@`, `press@`, `hello@`, `contact@`, `careers@` until actual need arises.

When provisioned, site updates needed:
- Privacy policy contact → `privacy@inknironapps.com`
- Author contact (book detail cards + home About section) → `riley@inknironapps.com`
- Apps Settings "Send Feedback" deep links → `support@inknironapps.com`
- Footer keeps `info@`
