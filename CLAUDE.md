# inknironapps-legal

Static legal pages (privacy policy, terms) for all Ink & Iron Apps products. Hosted via GitHub Pages at `lightwraith8268.github.io/inknironapps-legal/`.

## Branch strategy (overrides global rule)

**Commit and push directly to `main` for this repo.** This is a static-site Pages repo with no CI gates, no auto-merge workflow, and no `claude/dev` branch — the normal dev→PR→main pipeline doesn't apply here. Pushes to `main` deploy directly via GitHub Pages.

This overrides the global CLAUDE.md rule that says to push to `claude/dev`.

## Design system

The site uses `D:/Coding/inkironapps/brand/landing.html` as its visual basis. Palette, typography, monogram SVG, hero scaffolding, and section patterns are lifted from that file — do not invent new styling. Brand web assets (favicons, OG image, manifest, `icon.svg`, `logo.svg`) are copied from `D:/Coding/inkironapps/brand/web/` and `D:/Coding/inkironapps/brand/` into the repo root.
