---
name: company-setup
description: Turn a company name and website into a ready-to-review competitive tracker - profile, products, pricing, people, history, customer stories, competitors, channels, brand and news search terms. Use when starting to track a new company.
---

# Company setup

**Status:** built, in testing · **Feeds:** ideal-customer-profile, battlecard, this-is-that, company-timeline, release-note-trajectory

Give it a company (e.g. Buildkite, https://buildkite.com). It builds everything needed to start tracking that
company and its market, and proposes it all for human review. Nothing is tracked until it's approved.

## Inputs

- Company name and website (the website is found by search if missing)
- Optional: competitors you already know, how many competitors to keep (default: no limit), how many key
  people per company to research (default 5)

## What it collects

For the company **and every competitor it finds**:

| Area | Collected |
| --- | --- |
| Profile | Description, problem solved, categories, buyer, founding, HQ, size, business model, named customers, aliases |
| Products | Each product with former names, what it does, delivery model, launch date, lifecycle, docs/changelog/pricing links |
| Pricing | Plans per product: price, unit, billing, audience, limits |
| People | Leadership, founders, board, developer advocates, product leads, with titles |
| History | Dated events: founding, funding rounds, acquisitions, launches, renames, sunsets, leadership changes |
| Customer stories | Customer, industry, size, region, product used, problem, outcome, champion, quote |
| Brand | See [brand-guide](../brand-guide/SKILL.md) |
| People's views | See [person-perspective](../person-perspective/SKILL.md) |
| Channels | The company's podcasts, YouTube channel, blog, changelog, press page; active podcasts about its categories |

Then, for the tracked company: competitors **per product** (with which of its products each one competes with),
and news search terms for every company, product and key person.

## How it works

1. **Read the company's own site:** home page, then the about/leadership, product, pricing, customer and press
   pages it links to. Social links (YouTube, podcasts, GitHub, X, LinkedIn) are collected from the pages.
2. **Extract facts with an LLM using a fixed JSON schema** (structured outputs). Rules given to the model:
   - use only what the pages say, never outside knowledge; leave a field empty when it isn't stated
   - every fact cites the page it came from
   - products are distinct products, not features or plans; categories are market labels, not slogans
   - events are dated facts only
3. **Search for more people** (leadership, developer advocates, founders) and keep only those the results say
   currently work there. First names alone are dropped: they can't be matched reliably.
4. **Find competitors per product** from "alternatives", "competitors" and "vs" searches. Review sites,
   consultancies and integrations are excluded. Each competitor's own site is found and profiled the same way.
5. **Find channels:** the company's own shows in Apple's podcast directory (publisher must match), its YouTube
   channel, and recently active shows about its categories.
6. **Write search terms** in Google News syntax. Names that are common words get context
   (e.g. `"Harness" ("software delivery" OR CI)`).
7. **Propose everything** with its source page and a confidence level:
   - **high:** stated on the company's own page
   - **medium:** reported elsewhere
   - **low:** inferred
8. **Write a review page** in the company's own brand, listing everything with sources and what the run cost.

## Design decisions

- **Proposed → approved:** discovery is noisy, so a person approves before anything is tracked; rejected items
  are remembered so they aren't proposed again.
- **Provenance on every fact:** source URL, date first found, date last confirmed. Any claim that later lands in
  a battlecard can be traced and re-checked.
- **Re-runs merge, never overwrite:** a second run fills gaps and confirms facts but keeps human edits and approvals.
- **Each source is listed once,** tagged with every company it serves, so trackers never duplicate work.
- **Cost is metered per run:** model tokens, dollars and search credits, this run and month to date.

## Output

Records for companies, products, plans, people, events, customer stories, appearances and perspectives, all
proposed; proposed sources (podcasts, YouTube, feeds); a search-terms file; a brand guide per company; a review
page.
