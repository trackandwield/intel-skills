---
name: source-drift-check
description: Catch a tracked source going bad - drifting off topic, going quiet, or dropping in quality - so it's paused instead of silently filling the store with noise. Use periodically across all followed sources.
---

# Source drift and quality check

**Status:** designed

## How it works

Periodically sample each source's recent items and check them against the subjects it serves. Flag:
- a sustained drop in on-topic share
- a topic pivot
- a long silence
- repeated failures (already visible in the errors-and-flags report)

## Output

A list of flagged sources, each with its reason (drift, inactivity, quality) and a suggested action: pause,
remove or keep.
