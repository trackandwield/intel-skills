# Changelog

## 2026-10-14 (battlecard collection)

- **battlecard:** collection for the chosen competitors and sections: logos for every card header, reviews and
  community posts grouped into strengths and weaknesses, security and compliance facts from trust pages, and
  the pricing plans and customer stories company setup missed. Review quotes and compliance facts are checked
  word for word against their sources (the first piece of evidence-checks in use).

## 2026-10-13 (battlecard choices)

- **battlecard:** the user now chooses which competitors and which sections go on the cards, from an 18-section
  catalog with two presets (a seller's one-pager and a deep dive). Each section names the information it draws
  on, so the choice produces a collection plan: what's ready per competitor, and which collectors to build next.

## 2026-10-13 (confirmed websites, on-topic podcasts)

- **company-setup:** competitor websites are confirmed before use: the page must name the company and be judged to
  be its site against what it does. The clean Buildkite run still had Depot at `depot.com` and Blacksmith at
  `blacksmith.org`, because a guessed address was accepted when its title matched the name.
- **company-setup / source-discovery:** category podcasts are judged on their feed description and recent
  episodes. The run had proposed a security news show, a conversion-rate marketing show and an audiobook for
  "CI/CD", "test optimization" and "package management".

## 2026-10-13 (review page)

- **company-setup:** the review page is binned by company (tracked company first, then each competitor in its own
  collapsible section, direct before adjacent) instead of one long list per record type. Brand guides are read
  for the tracked company only; competitors don't need one, and skipping them saves a page fetch and a model call each.

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
