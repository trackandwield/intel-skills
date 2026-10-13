---
name: translation-fallback
description: Translate non-English articles to English using a free cloud allowance first and a local model when it runs out, tracking the allowance so the switch is automatic. Use for global coverage in any language.
---

# Translation with free-tier fallback

**Status:** built

## How it works

1. **Detect the language** from the text itself, using the source's own label only when there's too little text
   to judge.
2. **Translate with Azure AI Translator's free tier** (2 million characters a month) while the allowance lasts.
   - Azure can't report what's left, so usage is counted locally and resets on the billing day.
   - Requests are paced under the free tier's speed limit (about 33,300 characters a minute), so a big batch
     waits instead of being refused.
   - If Azure says "slow down", wait a minute and try once more.
3. **Fall back to a local model** (Ollama) when the allowance is used up or Azure refuses.
4. **If Azure says the quota is exhausted,** that's remembered until the reset day. That day, one tiny test
   translation confirms the credits are back before Azure is used again.
5. **Keep the original** alongside the translation, and mark items neither engine could translate as pending, so
   a later run picks them up.

## Cost practice

Translate titles and summaries first and full text only for items that matter. 2 million characters covers
roughly 100,000 titles, against a few hundred full articles.
