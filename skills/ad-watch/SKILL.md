---
name: ad-watch
description: Track what the companies you follow and their competitors advertise on podcasts (and video), as campaigns with their message, claims, offer and placements, and flag new campaigns and changes. Use after transcription, before embedding.
---

# Ad Watch

**Status:** built (podcasts and videos)

## How it works

1. **Find the ad breaks** in each transcript: anchored on what only ads say (a web address read out, a promo
   code, "brought to you by"), grown back over scripted sentences (ads have no "I mean", "you know", tag
   questions) up to a break line ("welcome back", "thanks for having us"), and filled across short scripted gaps
   between two ads (an ad that reads no address).
2. **Split each break into single ads:** at each address read out, and where the brand being named changes.
   Ads by companies nobody watches act as dividers.
3. **Match each ad to a watched company:** the companies marked tracked or competitor in the research store,
   with aliases, products and the ways speech recognition is known to mishear them, plus a manual list.
4. **Match it to the company's earlier ads by wording.** The same script is the same campaign: count it, and
   note the date, show and episode. A different script is a new campaign: a local model reads it (product,
   message, claims, offer, audience, call to action). A known script with a new offer or product is a change,
   kept in the campaign's history.
5. **Surface it:** new campaigns and changes go on the company's timeline and into the day's report; all
   campaigns are in the company's records.

Ads are also kept out of the searchable conversation, so a company counts as discussed only when people
actually talked about it, while who advertises where stays searchable on its own.

## Output

One row per campaign: company, product, message, claims, offer, audience, call to action, latest wording,
shows, first and last heard, times heard, episodes, history of changes.

## Later

- Spend estimates from placements (show size × frequency).
- Comparing a company's ad claims with its own site and with what reviewers say (evidence checks).
