# bestshowerkit.com

Static site for Best Shower Kit. Deploys to GitHub Pages. No build step — every page is plain HTML.

## Structure

```
/                               Walk-in shower kits (home)
/best-shower-kits/              Buyer's guide — primary "best shower kit" target
/bestbath-shower-kits/          Bestbath dealer page, full product line
/shower-kits-for-seniors/       Accessible showers / aging in place
/custom-shower-kits/            Custom sizes, colors, drain positions
/shower-kit-materials/          Fiberglass vs acrylic vs solid surface vs tile
/shower-sizes/                  Sizes + kit builder
/barrier-free-shower-kits/      Barrier-free range
/shower-pans/                   Pans only
/shower-wall-panels/            Wall systems
/tub-to-shower-conversion/      Conversions
/walk-in-shower-cost/           Cost + estimator
/shower-installation/           Install guide
/commercial-ada-showers/        ADA / commercial
/blog/                          Guides index
  /blog/shower-kit-buying-mistakes/
  /blog/curbless-shower-existing-floor/
  /blog/walk-in-shower-vs-walk-in-tub/
/sitemap.html                   Human sitemap
```

## Shared assets

- `assets/base.css` — design tokens and base components.
- `assets/theme.css` — color, depth and the shared components used by the 2026 pages.
  Loaded **after** the base styles on every page. Edit this file to restyle the whole site.

Older pages still carry a copy of the base styles inline; they also link `theme.css`,
which overrides them. New pages link both stylesheets and carry no inline base CSS.

## Conventions

- Logo is 300 × 94 everywhere (header, footer, Organization schema).
- Every dimension is wrapped in `.dim` so it renders in the mono spec-sheet face.
- Every page carries: an `.aistrip` "In short" summary, a visually hidden
  `.sr-only` fact sheet for answer engines, and JSON-LD (Organization,
  BreadcrumbList, WebPage/BlogPosting, FAQPage where relevant).
- Quote form posts to formsubmit.co; the address is assembled at submit time.
- US English spelling throughout.
- `.callbar` is a sticky call/quote bar shown below 760px.

## Interactive tools

| Page | Tool | Element |
|---|---|---|
| `/best-shower-kits/` | 60-second kit finder | `.chooser[data-chooser]` + `window.showerResult` |
| `/shower-kits-for-seniors/` | Bathroom safety check | `.chooser[data-chooser]` + `window.showerResult` |
| `/custom-shower-kits/` | Custom fit checker | `#fitTool` / `#fitGo` |
| `/shower-kit-materials/` | Material tabs | `[data-tabs]` / `[data-tab]` / `[data-panel]` |

Generic handlers for reveal, tabs and choosers live in the inline script at the
bottom of each page. A page that needs a chooser defines `window.showerResult(answers)`
before that script.

## Before publishing

Update `sitemap.xml` and `sitemap.html` when a page is added. Do not list a URL in
`sitemap.xml` before it returns 200 — the utility pages are commented out for that reason.
