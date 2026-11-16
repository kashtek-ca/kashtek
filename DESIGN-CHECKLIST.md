# kashtek.ca design checklist

Combined from "Unslop AI-Generated UI Designs" (20 tactical fixes) and Google's Modern Web Guidance (semantic HTML, accessibility, performance, metadata). Run it before any push. Visual identity stays fixed: Understory palette, Bricolage Grotesque + Instrument Sans, single amber accent.

## Content and copy
1. No emojis, no exclamation marks, no filler badges or decorative labels.
2. Every headline says something specific about Kashtek; no generic "solutions" headlines.
3. Italics only on the one accent word in a display headline (the `em` pattern); never in body copy.
4. Prices, rates and contact details match services.html, terms.html and llms.txt exactly.
5. One primary CTA per section, worded the same way ("Start a conversation").

## Typography and spacing
6. Display headlines use `text-wrap:balance` and sit at the largest size on the page.
7. Body copy 16px or larger, line length at most about 65ch.
8. Spacing groups related things: tighter inside a card, larger between sections, all from the existing clamp() scale.
9. Optical alignment over pixel alignment: check headlines, buttons and card edges by eye at 390 and 1280.
10. Nested radii follow outer minus padding; reuse the existing 8 / 14 / 20 radius set only.

## Colour and contrast
11. Body text 4.5:1 or better against its background, including text over photos (check the gradient, not the photo).
12. Amber accent is the only accent; `--accent-ink` on amber fills.
13. Links in running text are distinguishable without colour alone (underline).

## Structure and accessibility
14. One `h1` per page, headings in order, one `main` landmark with id `main`, `nav` labelled.
15. Skip link as the first focusable element.
16. Every interactive element has a visible `:focus-visible` state and a 44px touch target.
17. Repeated link text ("Learn more") carries an `aria-label` naming its target.
18. Decorative images use `alt=""`; informative images get real alt text.
19. Mobile menu: `aria-expanded` + `aria-controls`, closes on Escape and on link click.
20. Content must not depend on JS: `.reveal` has a `noscript` fallback and honours `prefers-reduced-motion`.
21. Anchored sections clear the fixed nav (`scroll-margin-top`).

## Performance and responsive
22. Raster images have a `-mobile` variant via `srcset`/`sizes`; below-fold images `loading="lazy"`, the LCP image `fetchpriority="high"`.
23. No horizontal scroll at 390px; test at 390 and 1280.
24. No frameworks, build steps or third-party scripts; fonts only via the existing Google Fonts link with `display=swap`.
25. `color-scheme:dark` declared so native controls and scrollbars match.

## Metadata and discovery
26. Each indexable page: unique `title`, `description` (about 160 characters or fewer), canonical, Open Graph and Twitter card tags, theme-color.
27. Legal pages and 404 carry `noindex`; indexable pages are listed in `sitemap.xml`; `robots.txt` points to it.
28. JSON-LD on the home page matches visible content.
29. Icons: favicon + apple-touch-icon on every page.
30. Show the real thing: use real photography and real service content, not placeholder blocks.

---

## Audit, 2026-11-16 (index, services, events, privacy, terms, refund-policy, 404)

30 items. Before fixes: 18 pass, 11 fail (11, 13-17, 19-21, 25, 27), 1 n/a. After fixes: all fails fixed; two small items left open (WebP/AVIF, `og:image:alt`), noted under 22 and 26.

| # | Result before | Note |
|---|---|---|
| 1-3 | pass | No emojis or "!"; italics only on accent words |
| 4 | pass | Prices and contact consistent |
| 5 | pass | CTA wording consistent |
| 6-10 | pass | Clamp scale and radii consistent (14px cells, 20px panels) |
| 11 | FAIL index | Body text in the AI bento card over the photo was low contrast; text brightened, gradient deepened |
| 12 | pass | |
| 13 | FAIL legal pages | Prose links only had a hover border; now underlined |
| 14 | FAIL index, services | No `main` landmark; added. Events, 404 and legal pages already had one |
| 15 | FAIL all | No skip link; added |
| 16 | FAIL all | Menu button under 44px, footer links short; fixed |
| 17 | FAIL index | Four identical "Learn more" links; aria-labels added |
| 18 | pass | All images decorative, `alt=""` |
| 19 | FAIL all | No aria-controls, Escape or close-on-click; added |
| 20 | FAIL all | Reveal content invisible without JS; noscript fallback added |
| 21 | FAIL all | Fixed nav covered anchor targets; scroll-margin added |
| 22 | pass | srcset, lazy, fetchpriority present. Open: JPEG only, no WebP/AVIF |
| 23 | pass | No horizontal scroll on any page at 390 or 1280 |
| 24 | pass | |
| 25 | FAIL all | Added `color-scheme:dark` |
| 26 | pass | Index description was about 215 characters; shortened. Open: no `og:image:alt` (needs image inspection). Legal pages have no OG tags by design (noindex) |
| 27 | FAIL | No sitemap.xml or robots.txt; added |
| 28-29 | pass | |
| 30 | n/a | Applies to index and services only, which pass |
