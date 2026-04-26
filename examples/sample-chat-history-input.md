# Sample Chat History Input

This file shows what a chat history input looks like when using **Mode 1: Advisor Priority Extraction** from written messages rather than transcripts.

Chat logs and WeChat/email exchanges can be used the same way as meeting transcripts. The extraction logic is the same: look for recurring patterns, not one-off corrections.

---

## Example Chat Exchange (Illustrative)

The following is a representative sample based on common lab communication patterns.

---

**[WeChat — after submitting a draft section]**

Advisor: 你把所有传感器都说成有这个问题了，这样不行。有些传感器根本就没有这个问题。你要把范围缩小，然后加一个citation来支持。

Student: 好，我去改。

---

**[WeChat — two days later, revised draft submitted]**

Advisor: 我还是看到同样的问题在另一段里面。你审稿之前有没有通读一遍？

Student: 读了两遍。

Advisor: 以后发给我之前你要把整篇文章从头到尾检查一遍，特别是前后逻辑一致不一致。

---

**[Email — reviewer response draft]**

Advisor: 你每个response前面都说谢谢，这个不对。谢谢只在每个reviewer最后说一遍，其他地方不用说。而且你对第三条reviewer 2的意见没有回应，这个一定要补上。

---

## What Mode 1 Would Extract from This

**Pattern: Overgeneralization** (High confidence — appears in transcript set AND chat)
- Scoping a claim to specific conditions and adding a citation is consistently required

**Pattern: Read before sending** (High confidence — multiple instances)
- Not just "I read it" but full front-to-back consistency check before each submission

**Pattern: Reviewer response format** (High confidence)
- Gratitude once per reviewer, at the very end
- Every comment must be addressed — ignoring any is not acceptable

---

## How to Provide Your Own Chat History

Copy and paste the relevant exchanges. You do not need to format them in a specific way. Include enough context so the pattern can be distinguished from a one-time situational comment. Three or more instances of the same feedback create a reliable pattern; a single instance is noted but marked low-confidence.
