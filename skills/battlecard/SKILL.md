---
name: battlecard
description: Draft a battlecard (or one-pager, comparison, talking points) comparing a company's product with a competitor's, built only from current, sourced facts and laid out in the company's brand, with every claim traceable. Use when preparing sales or marketing material for a head-to-head.
---

# Battlecard (grounded asset generation)

**Status:** built, in testing (collecting at setup, browsing, building in brand or sample style, prompt export) · **Needs:** company-setup, this-is-that, ideal-customer-profile, fact-freshness, brand-guide

## Inputs

- **Competitors, chosen by the user** from the ones company-setup found (direct and adjacent), by name or by tier.
  Each card is the tracked company vs one competitor, product by product (from the "competes with" links).
- **Sections, chosen by the user** from the catalog below, or a preset: **rep** (a seller's one-pager for a live
  call) or **deep** (everything, for product marketing). Header and sources are on every card.
- **Audience:** e.g. CTO, CFO, engineering manager. The same facts are framed differently for each: cost and ROI
  for a CFO, architecture and integration for a CTO.
- **Style:** the tracked company's brand guide, or **the user's own sample battlecards** (HTML, Markdown, Word,
  PowerPoint, PDF, images), which become the style guide.

## Collect first, build on request

Everything a card can use is collected when the company is set up, kept, and shown on one browse page, binned
by company, with the source of every fact. The user ticks the companies and metrics (sections) they care about
and reads the facts directly; no card is built until they ask. The same selection then drives either way of
making cards.

## Section catalog

Each section names the kinds of information it draws on, so choosing sections also decides what to collect.

| Section | What goes in it | Draws on |
| --- | --- | --- |
| Header | Our product vs theirs, last updated, overall confidence | profile, products |
| Quick take | Why we win, why we lose, when to walk away | derived from the sections below |
| Who they are | What they do, their pitch, buyer, size, funding, momentum | profile, funding and hiring |
| How they position against us | Their comparison pages, their claims about us, messaging changes | comparison pages |
| Where we meet them | Overlapping segments; which of our products each of theirs competes with | products, customer stories |
| Feature comparison | Capability by capability, with sources | feature lists (shared vocabulary) |
| Pricing and packaging | Plans, units, free tier, enterprise terms, hidden costs | plans, pricing details |
| Their strengths | What they really do well | reviews and community, customer stories |
| Their weaknesses | Recurring complaints, outages, gaps | reviews and community, incident history |
| Landmine questions | Discovery questions that surface their weaknesses | derived |
| Objection handling | Likely objections, each with a response and proof | derived; comparison pages, win/loss notes |
| Proof points | Our customers who switched from them, with numbers and quotes | our customer stories |
| Switching | Effort to move from them to us; their lock-in | migration guides |
| Security and compliance | SOC 2, ISO, FedRAMP, self-hosting, residency, SSO | trust pages |
| Ecosystem | Integrations, marketplace, platform lock-in | integrations, portfolio graph |
| Recent moves | Launches, acquisitions, executive and price changes, last 90 days | timeline events |
| Their direction | What their leaders say; where their releases point | perspectives, release-note trajectory |
| Sources and freshness | Every claim's source and date; stale claims flagged | evidence checks |

## Planning the collection

For the chosen competitors and sections, a plan lists each section as **ready**, **partly** or **not yet** per
competitor, and the collectors still needed: ones that don't exist yet (reviews, comparison pages, trust pages,
feature lists...) and existing ones that found nothing for some competitors. Win/loss and field notes aren't on
the web and need an internal source.

## Collecting for the choice

Once competitors and sections are chosen, collection runs only what that choice needs, for those competitors:

- **Logo** for every card's header: the SVG or image in the competitor's site header (images in "trusted by"
  logo walls further down are ignored, since those are customers' logos), else its app icon. Saved inside the
  record so cards work offline.
- **Reviews and community:** review sites (G2, TrustRadius, Capterra, Gartner Peer Insights, PeerSpot) and
  developer communities (Reddit, Hacker News), grouped by a model into strengths and weaknesses by theme. Every
  quote must appear word for word in the result it cites, or the point is dropped. A theme backed by more
  sources counts more.
- **Security and compliance:** from the competitor's own trust or security page: certifications, privacy,
  SSO/SCIM, hosting options, data residency, each with the sentence that states it (checked against the page).
- **Gaps from setup:** pricing plans and customer stories where company setup found none.

Each collector runs once per competitor per month unless refreshed, so reruns cost only what's new, and the
spend is recorded per run.

## Two ways to make the cards

### 1. Built by the engine

One page per chosen competitor, the tracked company vs that competitor:

- **Data sections** (pricing, strengths, weaknesses, security, recent moves...) list the collected facts as they
  are, each numbered to its source, with a source list at the bottom of the card.
- **Written sections** (quick take, landmine questions, objection handling) are drafted by a model from the same
  numbered facts, both sides. Every point must cite the facts it rests on; points citing nothing (or a fact
  that doesn't exist) are dropped.
- **Empty sections say so** ("not collected yet: needs feature lists") instead of being filled in.
- **Styled** with the brand's colors, fonts, logo and voice, or with the samples' colors, fonts, own headings,
  section order, tone and length. Prints to one or two pages.

### 2. A prompt for any AI agent

A single prompt the user gives to whatever agent they use: the task and rules (use only these facts, cite them,
write "No data yet" for gaps, quote reviewers exactly), the card structure in order, the style guide (brand or
samples), and every fact grouped by company and section with numbered sources; plus an attachments folder with
both companies' logos and the sample cards. The agent can then lay the cards out in its own tools (slides,
documents) while staying grounded.

## Sample battlecards as the style guide

The user's own cards are read for what can be measured, in code: colors and fonts from HTML CSS, Word and
PowerPoint themes, and PDF font names; headings and their order from the document structure. A model then maps
each heading to a catalog section and describes the tone, length, layout and conventions to keep. Images can't
be read for text; they travel with the prompt instead.

## Output

The asset, plus a source list. Every factual claim links to its source and carries its last-confirmed date.
