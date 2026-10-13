---
name: duplicate-filter
description: Drop anything that has already come through - by id or by its tidied web address - so each article, video or episode is processed once, and remember when each source was last checked. Use right after the sources, before anything that costs time or money.
---

# Duplicate filter

**Status:** built

## How it works

- **Last check per source:** each feed or channel remembers when it was last read successfully. The next run only
  asks for newer items, plus a 6-hour overlap for posts a feed dates earlier than they appeared. A source that
  fails is checked from its own last good run, so nothing in between is skipped.
- **Seen before:** every item passed on is recorded. An item counts as already seen if either matches:
  - its id
  - its address with differences that don't change the article removed: http/https, `www.`, `#fragments`,
    trailing slashes, and tracking tags (utm_*, fbclid, and similar)

  That catches the same article arriving from an RSS feed and from a news search.
- Repeats within a single run are passed on once.
- Records older than a year are forgotten, to keep the store small.

## Output

The new items only. Every drop is recorded with what it matched, and shows up in the errors-and-flags report.
