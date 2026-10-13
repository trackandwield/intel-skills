---
name: this-is-that
description: Compare products and ideas on what they actually do - "this is that" for what they share, "this isn't that" for what sets them apart - to tell what's genuinely new from rebranding and to group products by likeness rather than by their makers' labels. Use when a new product appears or when comparing competitors.
---

# This is that / this isn't that

**Status:** designed · **Feeds:** battlecard, landscape-taxonomy, daily-findings-report

## Inputs

Products or ideas with their descriptions, docs, release notes and positioning: two to compare, or a set to group.

## How it works

1. **Compare on fixed dimensions,** not marketing language:
   - the problem solved
   - who it's for (buyer and user)
   - how it works (architecture, where it runs)
   - inputs and outputs
   - pricing model
   - integrations
2. **For each pair:**
   - **this is that:** the dimensions where they're equivalent, with evidence
   - **this isn't that:** the dimensions where they differ, and how
3. **Verdict on newness:** genuinely new, a variant of something existing, or renamed marketing, with the reasoning.
4. **Grouping:**
   - a cheap similarity pass proposes likely neighbours, so the model compares a handful of pairs, not every pair
   - products sharing the core dimensions form a group, and their differences become sub-groups or labels
   - borderline pairs are flagged for review instead of forced into a group
   - groups are revisited as new products arrive, since one newcomer can split or merge a group

## Output

- **Per pair:** the shared and differing dimensions with evidence, and a one-line verdict
- **Per group:** its members, the traits they share, and what sets each member apart
- **To the daily findings report:** new groups, groups that changed, and borderline pairs

## Rules

Dimensions are judged on evidence (docs, release notes, pricing pages), not taglines. Two products described with
the same buzzwords can be "this isn't that" on every dimension that matters.
