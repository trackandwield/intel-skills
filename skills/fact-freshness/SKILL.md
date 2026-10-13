---
name: fact-freshness
description: Confirm that the specific facts a draft uses are still true before it ships, re-checking only facts past the staleness window for their kind. Called by battlecard and other asset skills with the exact facts they used.
---

# Fact freshness and verification

**Status:** designed · **Called by:** battlecard

## How it works

It isn't a sweep of the whole store. An asset skill hands over the exact facts it used (claim, source, date last
confirmed). Each is checked against a staleness window for its kind:
- pricing and feature availability age in weeks
- leadership in months
- founding dates never

A fact past its window is re-checked live against its source, or against the newest collected content about that
company.

## Output

A status per fact: confirmed current, confirmed but aging, or stale/unconfirmed. The asset skill then keeps it,
swaps in a fresher fact, or flags the gap.
