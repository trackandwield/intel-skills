---
name: evidence-checks
description: Check concrete findings (titles, prices, dates, websites, products) cheaply and automatically - the quoted evidence must exist on the source page, pass rule checks, be supported according to an independent model, and agree with the rest of the records. Use on every extracted fact before it's proposed; judgment claims go to dialectic-verification instead.
---

# Evidence checks

**Status:** designed · **Uses:** every extractor (company-setup, person-perspective, release-note-trajectory)
· **Feeds:** dialectic-verification, claim-versioning, the review queue

Code has tests that pass or fail. Facts about companies don't, so extraction is designed to make most facts
testable: every finding comes with the exact words it rests on. The checks run cheapest first and stop at the
first failure.

## Inputs

A finding broken into atomic facts, each with its source URL, the stored page, a verbatim quote, and the date the
source gives (if any).

## The layers

1. **Quote check (code):** the quote appears on the stored page, word for word after whitespace is normalised.
   A fact whose quote can't be found is dropped, not reviewed.
2. **Rule checks (code), the equivalent of unit tests:**
   - the URL resolves and the page is text, not an image or PDF read as text
   - a website's domain matches the company's name
   - dates parse and are plausible (no launch before founding, nothing in the future)
   - prices have a currency, an amount and a unit
   - names are full names; no duplicate records by name or domain
3. **Grounding check (a different, cheaper model, can be local):** shown only the quote and the fact, it answers
   *supports*, *contradicts* or *not enough*. It never sees the extractor's reasoning, so it can't be led.
4. **Corroboration, for facts that go stale** (titles, "works there now", prices, plan limits): a second,
   independent source is looked for. Two agreeing sources raise confidence; a conflicting one is flagged.
5. **Consistency across the records, the equivalent of integration tests:** one current CEO per company, one
   current employer per person, a sunset after its launch, a renamed product not listed twice.

## Gold set

One hand-verified company (Buildkite) is kept as a fixture. Any change to a prompt, model or check is scored
against it per field (how many findings are right, how many are missed) before it's used. This is what makes it
safe to move extraction to a cheaper or local model.

## Learning from review

Every approve and reject is stored as a labelled example per field type. When the checks agree with the
reviewer often enough on a field type (e.g. 95%), facts of that type that pass every layer are approved
automatically, and a random sample is still audited to keep the agreement rate honest.

## Output

Per fact: passed, failed (which layer and why) or needs review, with a confidence level. Failures and review items
go to the errors-and-flags report.
