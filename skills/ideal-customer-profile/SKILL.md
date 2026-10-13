---
name: ideal-customer-profile
description: Build an ideal customer profile for each of a company's products from its own evidence - customer stories, pricing, positioning and who its people say they serve - with every trait traced to its sources. Use after company setup, and to compare who competing products are really for.
---

# Ideal customer profile (per product)

**Status:** designed · **Needs:** company-setup (customer stories, plans, positioning, people's views)

## Inputs

One product, and everything company setup collected about it:
- customer stories naming the product
- pricing plans
- the product's description and "who it's for" claims
- the company's buyer statement
- what its people say about whom they serve

## How it works

1. **Firmographics from customer stories:** count industries, company sizes and regions across the stories that
   use the product. Report counts, not adjectives ("5 of 8 stories: software companies with 500+ engineers").
2. **Buyer and user:**
   - the titles of the champions quoted in stories (who bought or championed it)
   - the people the product pages address (who uses it)
3. **Trigger and pain:** the "before" problems in the stories, grouped into a short list of recurring triggers
   (e.g. "builds over 30 minutes", "moving off Jenkins").
4. **Outcomes they buy for:** the measured results in the stories, grouped.
5. **Fit signals and anti-signals:**
   - **fit:** traits that predict a good fit, such as tech stack, team size, and regulated vs unregulated
   - **poor fit:** traits for which the pricing or positioning suggests it's the wrong product (e.g. a seat-based
     plan with a 50-user limit argues against very large teams on that plan)
5. **Confidence:** each trait carries how many sources support it. Traits backed by one story are marked
   tentative.
6. **Compare with competitors:** build the same profile for each competing product, then show where the ICPs
   overlap (head-to-head deals) and where they don't (each product's own territory).

## Output

Per product:
- a one-paragraph ICP statement
- a table of traits with evidence counts and links to sources
- triggers, outcomes, buyer and user titles, fit and poor-fit signals

Across competitors, an overlap view. Shaped so the battlecard skill can quote it.

## Rules

Only what the sources show. A trait with no source isn't written down. The ICP is a summary of evidence, not a
persona invented to fill a template.
