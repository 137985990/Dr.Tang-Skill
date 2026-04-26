# Sample Transcript Input

This file shows what a transcript input looks like when using **Mode 1: Advisor Priority Extraction**.

You would paste one or more transcripts like this into your prompt, then ask:

> "根据这些聊天记录提炼我导师最在意的点"

or

> "Extract my advisor's recurring priorities from these transcripts."

---

## Example Transcript (Illustrative)

The following is a representative sample drawn from real lab meeting patterns. Names and identifying details are changed.

---

**[Meeting transcript — paper introduction review]**

Advisor: 你这一段读起来没有一句话是错的，但是没有抓到东西。你想想，你每一段应该给我一句忠心思想。你读了这个，能不能在一句话之内告诉我这段想说什么？

Student: 就是说这个领域的数据采集很难？

Advisor: 对，但是你写出来的是一大堆事实的罗列，你没有告诉我为什么这是个问题。Something happening is not a problem, that's a fact. 你要解释为什么它是个问题，而且要有urgency。

---

**[Follow-up — same paper, next session]**

Advisor: 你这篇文章读了几遍？

Student: 两遍。

Advisor: 可能真不够。我经常做一天一页纸都没写出来，因为我读了又删，读了又删。你读不出来，你就找别人一起读，把那个感觉读出来。

---

**[Different session — reviewer response]**

Advisor: 这个评审的每一条你必须要回答，你不能忽略它。就算你不同意，你也要说你不同意，然后解释为什么。然后谢谢评审的话，你在每一个reviewer最后说一遍就行，不用每一条前面都说一遍。

---

## How Mode 1 Would Process This

Running Mode 1 on input like the above would produce output like:

**Recurring patterns identified:**
- Paragraph-level clarity: every paragraph must deliver one central thought
- Reading before sending: two passes is not enough; until the logic is tight, keep re-reading
- Reviewer responses: address every comment; gratitude once at end per reviewer

**Confidence:** High (all three appear in multiple distinct interactions)

---

## How to Provide Your Own Transcripts

Paste your transcripts directly in the prompt. No special formatting is required. The more distinct interactions you include, the stronger the pattern extraction will be. Aim for 3–5 distinct meetings or chat logs for a reliable profile.
