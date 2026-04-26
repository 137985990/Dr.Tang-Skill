# Demo Conversation

This file shows the skill being used end-to-end: Mode 1 (priority extraction) → Mode 2 (draft review) → Mode 3 (final send check).

The transcript excerpts are representative examples. The draft is a lightly modified version of a real introduction section. All identifying details have been changed.

---

## User Input

> 我准备把这段introduction发给导师了。先帮我从这些聊天记录里提炼一下她的要求，然后再审一下这段稿子。
>
> **聊天记录摘录：**
>
> [Meeting A — after submitting a draft]
> 导师：你这一段我读起来没有一句话是错的，但是没有抓到东西。你想想，每一段应该有一句忠心思想。你读了这段，能不能在一句话以内告诉我它想说什么？
> 学生：就是说采集的数据质量很差？
> 导师：对，但是你写的是一大堆事实罗列。你要告诉我为什么这是个问题，不是仅仅说它发生了。
>
> [Meeting B — reviewing a different section]
> 导师：你这里说"所有传感器都有电池问题"——你把全世界的传感器都打死了。有些传感器根本不耗电，你知道吗？这句话一定要加citation，而且要缩小范围。
> 学生：好的，我去改。
> 导师：而且这篇文章你读了几遍？读了两遍就发给我，真的不够。
>
> [Meeting C — reviewer response draft]
> 导师：你在每个response前面都说谢谢，这个不对。谢谢只在每个reviewer最后说一遍就行了。而且reviewer 2的第三条你没有回应——这个一定要补上，就算你不同意也要正面回答。
>
> **待审稿件（introduction第二段）：**
>
> "Fatigue detection has become increasingly important due to the development of wearable sensors. Multi-modal approaches using EEG, ECG, and other physiological signals have shown strong performance in controlled laboratory settings. However, sensor noise, battery limitations, missing segments, and individual channel differences make data collection challenging in real-world environments. The resulting data are richer but also noisier, making high-quality acquisition difficult. Most existing approaches treat fatigue detection as a multivariate time-series learning problem and rely on general-purpose temporal encoders."

---

## Skill Output

### Stage 1 — Advisor Priority Profile (Mode 1)

**Source material:** 3 meeting transcript excerpts

---

**Core Expectations**

- Every paragraph must deliver one clear central thought. Listing facts without arriving at an argument is the most consistent source of pushback. *[High confidence — Meeting A, pattern seen in multiple other sessions]*
- Strong claims require citations and precise scope. Broad assertions about "all sensors" or "always" will be challenged by reviewers who can cite counterexamples. *[High confidence — Meeting B]*
- Read the full document front-to-back before sending. Two passes is not enough. *[High confidence — Meeting B, mentioned across sessions]*

**Common Dissatisfaction Triggers**

- Paragraphs where every sentence is technically correct but the paragraph makes no overall point
- Overgeneralized claims without citations (e.g., "all sensors have X problem")
- Omitting a reviewer comment in the response — even if you disagree, you must address it

**Tone and Language Preferences**

- Diplomatic framing: flag limitations with scope, not sweeping condemnation
- Avoid language that "hits too broad a target" — critique should be precise

**Reviewer Response Preferences**

- Gratitude once per reviewer, at the very end only
- Address every comment individually — ignoring any is not acceptable

**Confidence Assessment**

- High confidence: central thought per paragraph, cite broad claims, read before sending, reviewer response format
- Medium confidence: diplomatic framing of limitations (fewer instances in this transcript set)
- Low confidence: none — all patterns in this set have multiple supporting instances

---

### Stage 2 — Draft Review (Mode 2)

**Draft:** Introduction paragraph on fatigue detection and multi-modal sensing

---

**Alignment with Advisor Expectations**

- The draft correctly identifies real-world deployment as the challenge area — this is the right domain
- The mention of multi-modal approaches sets up a reasonable context

**Top Risks**

1. **No central thought.** The paragraph lists five separate problems (noise, battery, missing segments, channel differences, noisy data) without resolving them into one argument. The advisor's question will be: "What's the one thing you want me to take from this paragraph?"

2. **"Battery limitations" is an unsupported overgeneralization.** Applied to sensors broadly without a citation. Some sensors are self-powered by motion or heartbeat; some biosignal sensors have negligible power draw. Without a citation and a scoped claim, this will be flagged in review.

3. **"The resulting data are richer but also noisier" is a contradiction without explanation.** "Richer" implies more information; "noisier" implies degraded usability. The relationship is not explained. Readers are left to resolve it themselves.

4. **No urgency at the end.** The paragraph describes challenges but does not close with a statement of why the gap matters. The advisor expects introduction paragraphs to end with urgency — not just "this is hard" but "this unresolved gap is a critical research agenda."

**Must-Fix Before Sending**

- [ ] Remove "battery limitations" or scope it: "certain wearable sensors face battery constraints [REF]"
- [ ] Replace the list-of-facts structure with one clear argument — define the single point this paragraph must make before rewriting
- [ ] Resolve or remove the "richer but also noisier" contradiction
- [ ] Add a closing sentence establishing urgency: why does it matter that the gap is unsolved?

**Suggested Improvements (Non-Blocking)**

- Consider splitting into two paragraphs: one establishing that multi-modal approaches work in lab settings, one establishing why they fail in deployment. Each paragraph gets one job.
- The final sentence about "general-purpose temporal encoders" is not connected to the challenge being described — either connect it or move it.

**Rewritten Passages**

*Opening sentence:*
- Original: "Fatigue detection has become increasingly important due to the development of wearable sensors."
- Suggested: "Fatigue detection is a safety-critical task with direct implications for accident prevention in transportation, aviation, and industrial operation."
- Reason: The advisor expects the opening to establish urgency through the application domain, not through a tool's development. "Due to the development of wearable sensors" attributes importance to the technology rather than to the human need.

*Closing sentence (currently absent):*
- Suggested: "Despite progress in controlled settings, reliable fatigue detection in real-world deployment remains an unsolved and urgent research challenge."
- Reason: The advisor explicitly expects the first-paragraph close to name the unresolved gap that motivates the paper. Without it, the paragraph is a description, not an argument.

*Battery claim:*
- Original: "sensor noise, battery limitations, missing segments, and individual channel differences"
- Suggested: "sensor noise, intermittent connectivity, signal degradation from motion artifacts, and missing data segments"
- Reason: "Battery limitations" overgeneralizes and requires a citation to defend. The substituted framing describes real-world conditions that apply broadly to wearable sensing without making a claim that requires evidence.

**Send Readiness**

**Not ready yet.**

The paragraph contains two must-fix issues that the advisor will reliably flag: no central argument delivered, and an unsupported overgeneralization. Both are in her high-frequency correction patterns. Resolve the must-fix items and re-read the paragraph once before sending.

---

### Stage 3 — Final Send Check (Mode 3, after revisions)

*(Run after applying the must-fix items above)*

**Readiness Label: Ready to send.**

No blocking issues detected in the revised version.

**Confidence Note:** Based on high-confidence patterns from 3 transcript excerpts. If the advisor's standards have shifted since these transcripts were recorded, that may not be reflected here.

---

## Key takeaway from this demo

The skill does not replace careful reading. It does two things the student cannot easily do alone:

1. It surfaces which of the advisor's expectations are *stable* (repeated across sessions) versus situational — so the student knows what to prioritize.
2. It applies those expectations to a specific draft — not to "good writing in general" — and flags only what is likely to cause a problem with this particular advisor.
