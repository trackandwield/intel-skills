---
name: transcription
description: Turn podcast audio and caption-less videos into timestamped transcripts on a local GPU, using free captions and publisher transcripts first, and catch misheard names. Use for every new episode that has no text yet.
---

# Transcription

**Status:** built for YouTube captions and podcast audio (local Whisper with name checks); publisher transcripts designed

## How it works

1. **Cheapest first:**
   - YouTube's own captions (built)
   - transcripts that podcast feeds link to (designed)
2. **Otherwise transcribe locally** with Whisper (faster-whisper, large-v3) on the GPU, with word-level timing and
   confidence. Delete the audio afterwards: the transcript is what's used, and audio is the expensive part to store.
3. **Give Whisper the episode's names first:** a short list (about 40 terms) from the show name, the title and the
   show notes, plus known names those mention. A long list makes Whisper worse, so the full vocabulary is used
   in the checks instead.
4. **Check the names it heard:**
   - Known names with the wrong spacing or capitals are fixed directly ("open ai" -> OpenAI).
   - Mishearings confirmed in earlier episodes are fixed directly.
   - Words that look or sound like a known name are found by comparing letters and a consonant "sound skeleton"
     ("wipe coding" and "vibe coding" sound the same). Checked against show-note names everywhere, and against
     the whole vocabulary only where Whisper was unsure of a word.
   - Each one is confirmed before it's applied: the stretch is transcribed again with the name expected, and
     the fix is made if Whisper now hears it; or the name is in the show notes and the match is very close; or a
     local model reviewing the sentence agrees. Unconfirmed ones are listed as suggestions, never applied.
   - A confirmed fix is applied everywhere the same words were heard.
5. **Learn:** confirmed mishearings are remembered with the name, so later episodes are fixed directly. Names
   nothing knows yet (CamelCase, acronyms, names with digits, Title Case phrases said twice or in the notes) are
   proposed for the vocabulary, for a person to approve or reject.
6. **Recheck old transcripts** against the current vocabulary when run again, without transcribing again.
7. **Log failures** so they show in the errors-and-flags report instead of disappearing.

## Where names come from

- The research store: every company, product and person, with aliases and former names.
- A vocabulary list that grows from transcripts (approved terms and how each has been misheard).
- Each episode's own title and show notes.

## Output

Per episode: the raw Whisper output (every word with timing and confidence), the corrected transcript (one
sentence per line, with times), and a correction log (heard -> now, and how it was confirmed), plus suggestions
and new terms. Same-episode-detection, person-perspective and extraction read the corrected text.

## Later

- Speaker labels (who said what).
- Learning across episodes: a term that turns up in several shows is surfaced as likely real.
