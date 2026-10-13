---
name: run-report
description: Produce the daily errors-and-flags report - every warning and error any step logged, how many items each step took in and passed on, and everything dropped as a duplicate, with the reason. Use at the end of a day's runs.
---

# Errors and flags report

**Status:** built

## What it shows

- Errors and warnings, grouped by step, with the steps that had errors expanded
- Each step's runs: time, items in, items passed on, items dropped
- Articles dropped as seen before, grouped by source, with what each matched and when it was first seen
- Videos and podcasts dropped as the same conversation: score, both titles, both openings side by side
- Near misses: pairs scoring just under the threshold, for tuning it
- Anything new that any step records appears automatically in its own section, so the report grows with the engine

## Planned

What extraction wasn't sure about (low-confidence facts), so they can be checked by hand.
