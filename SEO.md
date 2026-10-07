# SEO & Indexing — alireza-haeri.ir

Notes for crawling/indexing the portfolio page. **The profile `README.md` is intentionally left untouched** — this file holds everything SEO-related instead.

## Files served at the domain root

| File | Purpose |
| --- | --- |
| `index.html` | page + `<head>` meta + JSON-LD structured data |
| `robots.txt` | allows all crawlers, points to the sitemap |
| `sitemap.xml` | single-URL sitemap with `fa-IR` / `x-default` alternates |
| `site.webmanifest` | PWA manifest (name, icons, theme color) |
| `favicon.svg` · `favicon.ico` · `icon-96/192/512.png` · `apple-touch-icon.png` | site icons (Google results, iOS, Android) |
| `og-image.png` | 1200×630 social share card (Open Graph + Twitter) |
| `CNAME` | custom domain |

## In the `<head>`

- `title`, `description`, `author`, `robots` (`index, follow, max-image-preview:large, max-snippet:-1`)
- `canonical` + `hreflang` (`fa-IR`, `x-default`)
- Open Graph (`og:*`, including `og:image` 1200×630) and Twitter (`summary_large_image`)
- `theme-color` for light/dark, `rel="me"` identity links, `rel="manifest"`, `rel="sitemap"`
- `preconnect` / `dns-prefetch` hints for the font CDN, GitHub avatars and the GitHub stars API

## Structured data (JSON-LD `@graph`)

`Person` · `WebSite` · `ProfilePage` (with `primaryImageOfPage`) · two `ItemList`s — one for the open-source projects (`SoftwareSourceCode`), one for the Persian learning resources (`LearningResource`, `Course`).

Validate with the [Rich Results Test](https://search.google.com/test/rich-results) or [Schema Markup Validator](https://validator.schema.org/).

## Checklist to get indexed

1. **Google Search Console** — add the `https://alireza-haeri.ir` property, verify with a DNS TXT record (simplest for a custom domain), then *Sitemaps → submit* `https://alireza-haeri.ir/sitemap.xml` and use *URL Inspection → Request Indexing* once.
2. **Bing Webmaster Tools** — import the property from Search Console, submit the same sitemap.
3. **Social preview** — after a deploy, check <https://www.opengraph.xyz/> or the [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/) to confirm `og-image.png` renders.
4. **Keep dates fresh** — bump `<lastmod>` in `sitemap.xml` and `dateModified` in the JSON-LD when the page changes materially.
