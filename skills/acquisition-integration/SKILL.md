---
name: acquisition-integration
description: When a tracked company buys another, work out why and how the acquired product will fit into the buyer's lineup, predict the integration path, and follow whether that's what happens. Use when an acquisition is detected.
---

# Acquisition integration analysis

**Status:** designed · **Needs:** company-setup, this-is-that, release-note-trajectory

## How it works

1. **Detect** the acquisition from news alerts and press releases.
2. **Profile** the acquired company with company-setup: its products, people, customers and release history.
3. **Fit:** run this-is-that between the acquired products and the buyer's. Does it:
   - fill a gap
   - replace a weak product
   - add customers
   - add a team (an acqui-hire)
   - remove a competitor
4. **Predict the path,** with confidence:
   - folded into an existing product
   - renamed and kept as a new product
   - kept standalone
   - technology absorbed, product shut down
   - bundled into pricing
5. **Follow the signals** over the following months:
   - renaming
   - docs and domains moving or redirecting
   - pricing bundles
   - the acquired product's release notes speeding up or stopping
   - its people's new titles or departures

## Output

An acquisition record (date, price if public, rationale, predicted path), then a running log comparing the
prediction with what happened.

Worked example: Buildkite bought Packagecloud in 2023, and it became Package Registries: folded in and renamed.
