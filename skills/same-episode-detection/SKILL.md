---
name: same-episode-detection
description: Spot one conversation published twice - a podcast that also goes on YouTube - by comparing what is said, not titles, so it is transcribed and analysed once. Use after captions or transcripts are available.
---

# Same-episode detection

**Status:** built, in testing

## The problem

Many shows publish each conversation as both a podcast and a YouTube video, often under different titles and
days apart. Treating them as two items doubles transcription and analysis, and double-counts what was said.

## How it works

1. Take the opening of each transcript: the first 3,000 words, lowercased, with filler words ("um", "uh") removed.
2. Break it into overlapping runs of 5 words and hash each run.
3. **Score** = shared runs ÷ runs in the shorter opening.
   - The same conversation scores high even when caption and transcript wording differ slightly, or one version
     starts with a 2-minute ad.
   - Different episodes of the same show score near 0, even with a shared intro and sponsor read.
4. **Compare** each new episode with the others in the same run, and with episodes from earlier runs published
   within 10 days, since the two versions often go out days apart.
5. **At 0.2 or above,** the later one is dropped. When both arrive together, the YouTube version is kept: it has
   chapters and its captions came free. The kept item records where the other version lives.
6. **Pairs scoring between 0.05 and 0.2** are logged as near misses, so the threshold can be tuned against real pairs.

## Output

The items with duplicates removed; a record of each dropped pair (score, both titles, both openings) for the
errors-and-flags report.
