---
name: source-discovery
description: Find the podcasts, YouTube channels and feeds worth following for a company or idea - its own channels, its competitors', active shows about its space, and episodes its people appear in - and keep one master list so no two trackers follow the same source twice. Use when adding a company or idea, and periodically to catch new sources.
---

# Source discovery

**Status:** partly built (inside company-setup); standalone finders designed

## How it works

- **A finder per ingest type:** podcasts, YouTube, feeds, and more as new types are added.
- **Four kinds of source:**
  - the company's own
  - each competitor's own
  - active sources about the space
  - appearances by the company's people
- **Guest appearances become an episode watch, not a subscription:** one interview on someone else's show doesn't
  mean following every future episode. A show is proposed for a full subscription only if the company's people
  keep appearing on it, or it's clearly about the space.
- **One master list per source type:**
  - each source is listed once and tagged with every company or idea it serves
  - a company's own list is the master list filtered to that company
  - each source is fetched once per run, and its items are tagged for every subject that uses it
  - rejected sources are remembered, so they aren't proposed again
- **When finders run:** when a subject is added, when a new person gets a profile, and on a schedule (e.g. monthly).

## Output

Proposed sources in the master lists, each with the reason it was found, waiting for approval.
