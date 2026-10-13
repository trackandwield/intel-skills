---
name: release-note-trajectory
description: Collect a product's full release-note history and compare what it does today with where its changes point it next, stating each inference with evidence and a date so it can be scored later. Use for each tracked product.
---

# Release-note history and product trajectory

**Status:** designed · **Needs:** company-setup (changelog links)

## How it works

1. **Backfill once, then follow:**
   - collect every release note: all changelog pages, GitHub releases, docs "what's new" pages, launch posts
   - pull archived copies (Wayback Machine) for notes that were moved or deleted
   - after that, new notes come in with the regular runs
2. **Type each note:** product, date, change type (new capability, improvement, fix, integration, pricing or
   packaging, deprecation, AI feature), the area it touches, and the buyer it serves.
3. **Capability map:** what the product does now.
4. **Trajectory:** how the mix shifts over time (e.g. the share of AI entries per quarter, a new area getting
   steady releases, an old area going quiet), cross-checked against:
   - job postings
   - messaging changes
   - acquisitions
   - talks and interviews (person-perspective)
5. **Direction calls:** "heading toward X, based on these entries since March; medium confidence", dated and
   later scored against what actually ships.

## Output

A release history per product, a capability map, dated direction calls, and shifts sent to the daily findings
report.
