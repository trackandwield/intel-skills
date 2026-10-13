---
name: product-portfolio-graph
description: Map how a company's products relate to one another as a weighted graph - how closely each pair is used together, judged from integrations, shared data, bundling and customer evidence - plus a comparable feature list per product, so portfolios can be compared for cohesion and overlap. Use when analysing a company's product lineup or comparing lineups across competitors.
---

# Product portfolio graph

**Status:** designed · **Uses:** company-setup, release-note-trajectory, this-is-that · **Feeds:** battlecard,
ideal-customer-profile, acquisition-integration, product-sunset, company-timeline

Some companies sell a tightly connected suite: Adobe's Firefly is built into Photoshop, Illustrator and Express,
shares their files and accounts, and is sold in the same Creative Cloud plans. Others sell products that rarely
meet. This skill measures which kind of company it is, product by product, with the evidence behind each link.

## Inputs

- The company's products, plans, customer stories and release notes (from company setup and release-note history)
- Its docs: integration pages, "works with" pages, tutorials and workflow guides
- Optional: competitors to compare against

## How it works

1. **Products are the nodes.** Each carries its category, buyer and a feature list (step 4).
2. **Edges are weighted by evidence of joint use.** For each pair of products, collect the signals and score them:

   | Signal | Example | Strength |
   | --- | --- | --- |
   | One is built into the other | Firefly's generative fill inside Photoshop | strong |
   | Shared data, files, accounts or platform | the same assets library across apps | strong |
   | Documented native integration | a docs page connecting the two | strong |
   | Sold together | the same plan or bundle | medium |
   | Used together by named customers | a customer story naming both | medium |
   | Workflow guides that chain them | "design in A, then publish with B" | medium |
   | Release notes of one referencing the other | "now works with B" | medium; also shows the link growing |
   | Mentioned together in marketing only | a shared landing page | weak |

   The edge weight (0 to 1) combines the signals; repeated weak signals never add up to a strong one. Edges can
   have a direction when one product depends on or embeds the other. Each edge keeps its evidence list with
   sources and dates.
3. **Portfolio measures:**
   - **Cohesion:** how connected the lineup is overall (weighted density), so Adobe scores high and a holding
     company of unrelated products scores low
   - **Suites:** clusters of products that are used together
   - **Hubs:** the products everything else connects to (the anchor a buyer starts with)
   - **Islands:** products with weak or no links, often candidates for sale or sunset
   - **Overlap:** products in the same lineup with much the same features (possible cannibalisation or a
     consolidation coming)
4. **Feature lists that can be compared:** each product's features are extracted from its docs, pricing and
   release notes and mapped to a shared feature vocabulary (the landscape taxonomy), so "AI fill", "generative
   fill" and "content-aware fill" are compared as what they do, not by name. Features carry the plan they're in
   and the date they appeared. This gives:
   - a feature matrix across the company's own products (where they overlap, where they hand off)
   - a feature matrix against competitors' products, which battlecards and this-is-that use
5. **Snapshots over time:** the graph is saved per run, so links strengthening or fading show up: an acquired
   product being wired in, a product drifting away from the rest before it's retired.

## Rules

- No edge without evidence; every weight can be traced to its sources.
- A shared brand name is not a link. "Adobe X" and "Adobe Y" are connected only if they're used together.
- Features are compared by what they do, using this-is-that, not by what they're called.

## Output

- A graph per company (products, weighted edges with evidence), as data and as an interactive page
- A cohesion summary: score, suites, hubs, islands, overlaps, with what changed since the last run
- Feature matrices within the company and against competitors
- Changes (new links, fading links, new overlaps) go to the daily findings report
