---
name: person-perspective
description: Build a profile of a company's key people from what they say in public - the podcasts, videos, talks and articles they appear in - covering the problems they focus on and where they see the company heading. Use after company setup finds the people.
---

# Person perspective

**Status:** built, in testing · **Feeds:** battlecard, release-note-trajectory, daily-findings-report

## Inputs

A person (name, title, company) and their company's names and aliases.

## How it works

1. **Find appearances:**
   - podcast episodes from Apple's podcast directory
   - articles, interviews, talks and videos from a web search
   An appearance only counts when it names the person in full **and** names their company, so namesakes aren't
   picked up.
2. **Read the best sources,** up to 3 per person by default: article text, or a video's captions.
3. **Ask the model for their perspective,** using only what they said themselves (not the interviewer or narrator):
   - **Summary:** 2-3 sentences on what they talk about and believe
   - **Focus:** the problems they want to solve
   - **Outlook:** where they say the company or market is heading (left empty if they don't say)
   If the sources hold nothing the person said themselves, the perspective is left empty rather than filled
   with a note that there was nothing to say.
   - **Points:** theme, claim, exact short quote, source, date

## Output

- An appearances list per person (kind, title, show, date, link)
- Summary, focus and outlook on the person's profile
- One record per claim, each with its quote and source

## Why

What leaders say in long-form interviews often runs ahead of what the company announces. A CTO repeatedly
describing a problem is an early signal of where the product is going.
