---
name: dialectic-verification
description: Verify judgment claims (ideal customer profile, the problem a product solves, competitor tier, where a product is headed) with three agents - thesis makes the claim, antithesis tries to disprove it, synthesis resolves the two into a final sourced claim or escalates to a human. Use for any conclusion that can't be checked against a single quote.
---

# Dialectic verification (thesis, antithesis, synthesis)

**Status:** designed · **Uses:** evidence-checks, the ingest engine, company-setup · **Feeds:**
ideal-customer-profile, battlecard, this-is-that, release-note-trajectory, claim-versioning

Some conclusions have no single source that proves them: "Buildkite's ideal customer is a platform team at a
large company with a big monorepo" is an argument from many pieces of evidence. These are verified by argument:
one agent makes the case, a second tries to break it, and a third decides.

## Inputs

A question to answer (e.g. "the ICP for Buildkite Pipelines"), the records collected so far, and access to the
ingest engine's sources and search.

## The three agents

### Thesis

- Uses the existing pipeline (company setup, collected records, ingest engine) to make a first claim.
- Breaks the claim into **sub-claims**, each with its sources, verbatim quotes and dates. For example:
  - it sells to platform engineering teams
  - its customers are mostly large companies
  - monorepos are a central use case

  Sub-claims are what make the disagreement measurable.

### Antithesis

- Gets the claim, the sub-claims and their sources, but **not the thesis's reasoning**, so it isn't led to agree.
- Runs on a **different model** from the thesis (different model families share fewer blind spots) and does its
  own searching, through the ingest engine and the web, with several sources.
- Tries to disprove each sub-claim. Every objection must have a type and evidence:
  - **wrong entity:** wrong company, product or person
  - **missing source:** the page doesn't exist or doesn't say that
  - **contradicted:** another source says otherwise
  - **outdated:** newer evidence says something different (see claim-versioning)
  - **overgeneralised:** "large customers" from two logos
  - **better explanation:** the evidence fits another reading better
- Objections without evidence are discarded. "Could not refute" is a valid and expected answer; an agent told to
  find faults will otherwise invent them.

### Synthesis

- Gives each sub-claim a verdict: **upheld**, **revised**, **withdrawn** or **unresolved**, with reasons and the
  sources on each side.
- May do **one round** of targeted lookups to break ties on disputed sub-claims, then stops. This caps the cost
  and stops the agents from looping.
- Sorts every *contradicted* or *outdated* objection into **error** (the thesis's evidence never supported it) or
  **change** (it was true at its date and newer evidence differs), by comparing the dates on the evidence. Changes
  go to claim-versioning.
- Assembles the final claim from the verdicts, with its sources and a confidence level.

## When a human decides

Escalation depends on how far apart the agents ended up and how much the claim matters:

| Outcome | What happens |
| --- | --- |
| All sub-claims upheld, or revised in wording only | approved automatically |
| A minor sub-claim withdrawn | approved, noted in the findings report |
| A core sub-claim withdrawn, or any sub-claim unresolved | goes to review, with both sides laid out |
| Anything unresolved on a claim used in a battlecard or other shipped asset | always goes to review |

Each human decision is stored as a labelled example and used to tune these thresholds over time.

## Cost control

- Used only for judgment claims. Concrete facts go through evidence-checks, which is far cheaper.
- Thesis and antithesis can run on different providers, one of them a local model.
- Re-run only when a claim's evidence changes or its freshness window passes, not on every run.

## Output

The final claim with sub-claim verdicts, sources on both sides, confidence, any escalation, and the full exchange
kept for audit.
