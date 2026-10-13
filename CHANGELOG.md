# Changelog

## 2026-10-13 (verification)

- **evidence-checks:** new, designed. Layered checks for concrete facts: verbatim quote on the page, rule checks,
  a grounding check by an independent model, corroboration for facts that go stale, consistency across records,
  and a hand-verified gold set for regression testing.
- **dialectic-verification:** new, designed. Thesis, antithesis and synthesis agents for judgment claims, with
  typed, evidence-backed objections, one tie-break round, and escalation by how far apart the agents ended up.
- **claim-versioning:** new, designed. Validity periods on every claim, and a rule for telling an error from a
  real change, so changes become timeline history instead of overwrites.

## 2026-10-13 (product portfolio graph)

- **product-portfolio-graph:** new, designed. A weighted graph of how a company's products are used together
  (built-in, shared data, integrations, bundles, customer stories, release notes), portfolio cohesion, suites,
  hubs, islands and overlaps, plus feature lists mapped to a shared vocabulary for comparison within the company
  and against competitors.

## 2026-10-13 (review of the first full run)

Changed after reviewing the first complete Buildkite run (27 companies, about $2.90 in model calls):

- **company-setup:** a website found by search must be on the company's own domain (the run had matched Depot to
  Office Depot and Blacksmith to a clothing brand). Competitor names are tidied and duplicates merged by name or
  website. Image and PDF pages are skipped instead of read as text. Wrong matches can be rejected with
  everything found about them in one step.
- **brand-guide:** fonts come only from fonts the site loads (the run had picked Papyrus and an emoji font from
  CSS fallbacks); logos must be labelled as logos or be the inline SVG in the home link (the run had picked
  product screenshots); decks must name the company in full.
- **source-discovery / company-setup:** a company's podcast or YouTube channel must be published under its own
  name, so namesakes and fan shows are dropped.
- **person-perspective:** left empty when the sources hold nothing the person said, instead of a note saying so.

## 2026-10-13 (later)

- **company-setup:** competitors are now marked direct or adjacent, and only direct ones get the full profile.
  Products of large companies are read from their own product page. Runs save after each company and resume
  where they stopped. Changed after the first live run turned up 22 competitors, including Microsoft and
  JetBrains, and spent minutes profiling whole companies whose overlap was one product.
- **person-perspective:** YouTube Shorts no longer count as appearances.

## 2026-10-13

- First published set: 23 skills. Built: company setup, brand guide, person perspective, duplicate filter,
  same-episode detection, translation with free-tier fallback, errors-and-flags report; source discovery and
  transcription partly built. Designed: ideal customer profile, battlecard, this-is-that, release-note
  trajectory, acquisition integration, product sunset, company timeline, daily findings report, landscape
  taxonomy, category discovery, multi-category classifier, source drift check, preset watch, fact freshness.
