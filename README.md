# Intel skills

The skills and agents behind a competitive-intelligence engine I'm building: a system that, given a company,
maps its products, people, competitors and market, keeps following what's published about them (articles,
podcasts, videos, release notes, in any language), and turns that into sourced analysis: ideal customer
profiles, battlecards, product comparisons and where each company looks to be heading.

This repository holds the skill definitions only: what each one does, when it's used, what it takes in and
produces, and the rules it follows. The engine that runs them is private. Each skill's history in this repo
shows how it has evolved.

## Principles they share

- **Evidence over assertion:** every extracted fact keeps its source page, the date it was found and the date it
  was last confirmed; models are told to use only what the sources say and to leave gaps empty.
- **Proposed, then approved:** anything discovered (people, competitors, sources) waits for a human decision;
  rejections are remembered.
- **Free first, paid when it matters:** free sources and free tiers first, a local model as the fallback, and
  every paid call metered.
- **Built to be pointed at any market:** started on the AI landscape, then on developer tooling companies.

## The skills

### Collect

| Skill | What it does | Status |
| --- | --- | --- |
| [Company setup](skills/company-setup/SKILL.md) | Turn a company name and website into a ready-to-review competitive tracker. | built, in testing |
| [Brand guide](skills/brand-guide/SKILL.md) | Read a company's visual identity and writing voice from its website. | built, in testing |
| [Person perspective](skills/person-perspective/SKILL.md) | Build a profile of a company's key people from what they say in public. | built, in testing |
| [Source discovery](skills/source-discovery/SKILL.md) | Find the podcasts, YouTube channels and feeds worth following for a company or idea. | partly built (inside company-setup); standalone finders designed |
| [Duplicate filter](skills/duplicate-filter/SKILL.md) | Drop anything that has already come through. | built |
| [Same-episode detection](skills/same-episode-detection/SKILL.md) | Spot one conversation published twice. | built, in testing |
| [Translation with free-tier fallback](skills/translation-fallback/SKILL.md) | Translate non-English articles to English using a free cloud allowance first and a local model when it runs out, tracking the allowance so the switch is automatic. | built |
| [Transcription](skills/transcription/SKILL.md) | Turn podcast audio and caption-less videos into timestamped transcripts on a local GPU, using free captions and publisher transcripts first. | partly built (YouTube captions); local speech-to-text designed |
| [Errors and flags report](skills/run-report/SKILL.md) | Produce the daily errors-and-flags report. | built |

### Analyse

| Skill | What it does | Status |
| --- | --- | --- |
| [Ideal customer profile (per product)](skills/ideal-customer-profile/SKILL.md) | Build an ideal customer profile for each of a company's products from its own evidence. | designed |
| [Battlecard (grounded asset generation)](skills/battlecard/SKILL.md) | Draft a battlecard (or one-pager, comparison, talking points) comparing a company's product with a competitor's, built only from current, sourced facts and laid out in the company's brand, with every claim traceable. The user picks the competitors and sections, then has the engine build the cards (brand or sample style) or exports a prompt for any AI agent. | built, in testing |
| [This is that / this isn't that](skills/this-is-that/SKILL.md) | Compare products and ideas on what they actually do. | designed |
| [Product portfolio graph](skills/product-portfolio-graph/SKILL.md) | Map how a company's products relate as a weighted graph of how closely they're used together, with a comparable feature list per product, to measure how cohesive a lineup is and where products overlap. | designed |
| [Release-note history and product trajectory](skills/release-note-trajectory/SKILL.md) | Collect a product's full release-note history and compare what it does today with where its changes point it next, stating each inference with evidence and a date so it can be scored later. | designed |
| [Acquisition integration analysis](skills/acquisition-integration/SKILL.md) | When a tracked company buys another, work out why and how the acquired product will fit into the buyer's lineup, predict the integration path, and follow whether that's what happens. | designed |
| [Product sunset analysis](skills/product-sunset/SKILL.md) | Notice when a company retires a product or feature and work out what it says about where the company is heading. | designed |
| [Company timeline](skills/company-timeline/SKILL.md) | Draw an overhead timeline of a company. | designed |
| [Daily findings report](skills/daily-findings-report/SKILL.md) | Produce the daily report of what's new and worth knowing about each tracked company and its market. | designed |

### Organise and verify

| Skill | What it does | Status |
| --- | --- | --- |
| [Landscape taxonomy](skills/landscape-taxonomy/SKILL.md) | Maintain a living map of a market's categories, subcategories and terms, updated as new terms surface in what's collected, so every other skill classifies against the same map. | designed |
| [Category discovery](skills/category-discovery/SKILL.md) | Spot a new category forming before anyone names it, from several independent sources discussing something that doesn't fit the existing map. | designed |
| [Multi-category classifier](skills/multi-category-classifier/SKILL.md) | Tag a product or idea with every category it truly belongs to, not just the best single fit, so search and comparison never miss it. | designed |
| [Source drift and quality check](skills/source-drift-check/SKILL.md) | Catch a tracked source going bad. | designed |
| [Preset watch](skills/preset-watch/SKILL.md) | Keep a standing watch on one named company, person or topic across every collected source, catching even passing mentions inside broader content. | designed |
| [Evidence checks](skills/evidence-checks/SKILL.md) | Check concrete facts automatically: the quoted evidence must be on the page, pass rule checks, be supported according to an independent model and agree with the other records, scored against a hand-verified gold set. | designed |
| [Dialectic verification](skills/dialectic-verification/SKILL.md) | Verify judgment claims with three agents: thesis makes the claim, antithesis (on a different model) tries to disprove each sub-claim with evidence, synthesis resolves them or escalates to a human. | designed |
| [Claim versioning](skills/claim-versioning/SKILL.md) | Keep every claim with the period it was true, so a real change is recorded as history and a mistake as a correction. | designed |
| [Fact freshness and verification](skills/fact-freshness/SKILL.md) | Confirm that the specific facts a draft uses are still true before it ships, re-checking only facts past the staleness window for their kind. Called by battlecard and other asset skills with the exact facts they used. | designed |

**Status key:** *built* runs in the engine; *in testing* is built but still being tuned on real data; *designed*
is specified here and not yet built.

## Format

Each skill is a folder with a `SKILL.md` in the Claude skill format: a name and a description of when to use it,
then the instructions. See [CHANGELOG.md](CHANGELOG.md) for what changed and when.
