---
name: brand-guide
description: Read a company's visual identity and writing voice from its website - colors, fonts, logos, brand-asset files, published decks, tone - so assets and reports about it can match its brand. Use during company setup or before drafting a branded asset.
---

# Brand guide

**Status:** built, in testing · **Used by:** company-setup, battlecard, every company report

## Inputs

The company's website (home page and its stylesheets), plus any brand-assets or press-kit page it links to.

## What it collects

| Element | How it's found |
| --- | --- |
| Brand colors | CSS variables named primary/brand/accent first, then the most-used saturated colors in the stylesheets; the page's theme color |
| Neutrals | Greys and near-black/white, kept apart from brand colors |
| Fonts | Heading and body fonts, chosen only from fonts the site actually loads (Google Fonts, @font-face), so fallbacks and emoji fonts in the CSS are ignored |
| Logos | The inline SVG in the home link, header images whose file name, alt text, class or id says logo/wordmark/brandmark, the site icon, the social preview image |
| Brand assets | Downloadable files (SVG, PNG, ZIP, PDF, decks) on a brand-assets or press-kit page |
| Published decks | Speaker Deck, SlideShare and PDF results whose title names the company in full |
| Voice | Tagline, 3-6 adjectives, tone notes, words it repeats, real headlines quoted from its pages (LLM reading of home and about pages) |

## Applying it

Reports about the company are drawn with its brand:
- **Accent:** its first brand color that keeps at least 3:1 contrast on the page background, chosen separately
  for light and dark mode.
- **Fonts:** its heading and body fonts.
- **Logo:** in the header.

## Limits

- Colors and fonts come from what the site's CSS declares, so a site that draws its brand mostly in images will
  show fewer colors.
- Official brand guidelines, when a brand page links them, take precedence over what's inferred here.
