---
name: claim-versioning
description: Keep every fact and claim with the period it was true, so a legitimate change (new CEO, rename, price change, a shifting ICP) is recorded as history rather than treated as an error or overwritten. Use whenever a check finds newer evidence that differs from a stored claim.
---

# Claim versioning

**Status:** designed · **Uses:** evidence-checks, dialectic-verification, fact-freshness · **Feeds:**
company-timeline, release-note-trajectory, product-sunset, acquisition-integration, daily-findings-report

Verification asks "is this true?". Tracking a market also needs "*was* it true, and is it *still* true?". Without
dates, newer evidence that differs looks like the old claim was wrong. With dates, it's history.

## How claims are stored

Every fact and claim keeps:

- **valid from / valid to:** when it was true in the world (as far as the evidence shows)
- **learned on / last confirmed:** when the engine found it and last checked it
- its evidence and the verification that passed it

A claim is never overwritten. When it stops being true it's **closed** (valid to is set) and a new version is
**opened**.

## Error or change

When newer evidence differs from a stored claim, the dates on the evidence decide:

- **Error:** the stored claim's evidence never supported it. It's corrected and the mistake is logged against the
  check or model that let it through.
- **Change:** the old evidence was right at its date and newer evidence differs. The old version is closed, the
  new one opened, and the change becomes an event on the company timeline.

A change needs more proof than a first finding: a dated, authoritative source (the company's own page, a press
release, an official announcement). A single article saying "former CTO" makes it a **possible change**, flagged
until confirmed.

## What triggers a re-check

- **Schedule:** fact-freshness windows per fact type, short for prices, plans and titles, long for founding facts.
- **Events:** the ingest engine collects something that bears on a stored claim (an article about a leadership
  change, a release note renaming a product, a pricing page that changed). The related claims are reopened.

On a re-check, the current claim becomes the thesis and dialectic-verification asks whether it still holds.

## Drift in judgment claims

Judgment claims (an ICP, a product's positioning) usually drift rather than flip. Each version is kept, and the
differences between versions are reported as a trajectory ("moving upmarket since spring, based on these
changes"), not as corrections.

## Output

A versioned history per claim; change events for the company timeline and daily findings report; possible
changes in the review queue; and an error log per check and model, used to improve them.
