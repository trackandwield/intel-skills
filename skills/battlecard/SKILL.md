---
name: battlecard
description: Draft a battlecard (or one-pager, comparison, talking points) comparing a company's product with a competitor's, built only from current, sourced facts and laid out in the company's brand, with every claim traceable. Use when preparing sales or marketing material for a head-to-head.
---

# Battlecard (grounded asset generation)

**Status:** choosing built (competitors, sections, collection plan); drafting designed · **Needs:** company-setup, this-is-that, ideal-customer-profile, fact-freshness, brand-guide

## Inputs

- **Competitors, chosen by the user** from the ones company-setup found (direct and adjacent), by name or by tier.
  Each card is the tracked company vs one competitor, product by product (from the "competes with" links).
- **Sections, chosen by the user** from the catalog below, or a preset: **rep** (a seller's one-pager for a live
  call) or **deep** (everything, for product marketing). Header and sources are on every card.
- **Audience:** e.g. CTO, CFO, engineering manager. The same facts are framed differently for each: cost and ROI
  for a CFO, architecture and integration for a CTO.
- **Example assets:** past assets of that type, so the draft follows an established format and voice

The choice is saved per tracked company, and a picker page shows, for each competitor, how many of the chosen
sections have data today.

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

## How it works

1. **Retrieve** the structured facts for both products, filtered by audience relevance.
2. **Draft** against the example assets, so the format stays fixed and only the content is written.
3. **Check freshness:** hand the exact list of facts used (claim, source, date) to fact-freshness, which
   re-checks anything past its staleness window. Pricing and features age fast; founding dates don't.
4. **Flag** any claim that couldn't be verified, instead of shipping it silently.
5. **Lay it out** in the company's brand (brand-guide).

## Output

The asset, plus a source list. Every factual claim links to its source and carries its last-confirmed date.
