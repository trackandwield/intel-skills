---
name: transcription
description: Turn podcast audio and caption-less videos into timestamped transcripts on a local GPU, using free captions and publisher transcripts first. Use for every new episode that has no text yet.
---

# Transcription

**Status:** partly built (YouTube captions); local speech-to-text designed

## How it works

1. **Cheapest first:**
   - YouTube's own captions (built)
   - transcripts that podcast feeds link to (designed)
2. **Otherwise transcribe locally** with Whisper (faster-whisper) on the GPU. Delete the audio afterwards: the
   transcript is what's used, and audio is the expensive part to store.
3. **Log failures** so they show in the errors-and-flags report instead of disappearing.

## Output

A timestamped transcript per episode, which same-episode-detection, person-perspective and extraction all read.
