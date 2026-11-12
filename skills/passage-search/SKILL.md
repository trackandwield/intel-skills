---
name: passage-search
description: Make transcripts and articles searchable by meaning and exact names, as timestamped passages tagged with the companies, products and people they mention. Use as the last processing step of every run, and to answer questions from the collected material.
---

# Passage Search

**Status:** built (podcasts and videos; articles once full-text extraction is in)

## How it works

1. **Cut text into passages** of about 350 words at sentence breaks, overlapping by a sentence or two, each
   keeping the time it starts at (estimated within the speech recognizer's segments).
2. **Keep ads apart:** sponsor reads and credits become their own passages, flagged as ads, so an ad break never
   mixes into the conversation around it. Searches skip them unless asked.
3. **Two indexes per passage:** an embedding (meaning) from a local model, and a keyword index, because
   embeddings blur exact names ("IREN", "Talarico"). Searches combine both (reciprocal rank fusion).
4. **Tag each passage** with show, episode, date, link, subjects, kind (podcast, video, article), and the
   companies, products, people and terms it mentions, from the research store and the vocabulary, so a search
   can be filtered ("what was said about X since Monday").
5. **One collection for every kind of source**, so one search covers podcasts, video and articles; facts
   extracted later go to their own collections with the same tags.
6. **Re-runs are cheap:** an item whose text hasn't changed is skipped; a corrected transcript replaces its old
   passages.

## Output

Search results with the passage, show, episode, date, time in the episode (a link that opens there where
the site allows), and names mentioned; a list of who sponsors which shows.
