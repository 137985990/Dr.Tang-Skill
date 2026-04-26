# Design Notes

This document records decisions made during the design of the `Dr.Tang-Skill` and the reasoning behind them.

---

## Why Three Modes

The skill separates extraction (Mode 1), review (Mode 2), and pre-send check (Mode 3) because these are genuinely different tasks with different inputs and different output needs.

A student who has transcripts and a draft needs a full two-stage process: extract advisor priorities from historical material, then apply those priorities to the current draft. A student who just needs a final go/no-go before hitting send does not want a full profile extraction — they need a focused blocking-issues check.

Separating the modes also allows the advisor profile to be built once and reused across multiple drafts without re-running the extraction each time.

---

## Why Evidence Rules Are Explicit

The skill explicitly states: never invent preferences. This constraint was added because a skill that generates plausible-sounding but unsupported "advisor preferences" would be worse than no skill at all — it would mislead the student into preparing for feedback that will never come, and missing feedback that will.

The rule "a single comment is not a rule" is equally important. Advisors react differently to different document types, deadlines, and audiences. Only patterns that appear across multiple distinct interactions represent stable expectations.

---

## Why the Known Advisor Patterns Section Exists

The Known Dr. Tang Patterns section was populated from a corpus of 40+ meeting transcripts and contains only patterns that appear in multiple distinct interactions. It exists so that the skill can function as a useful reviewer even when the user provides no historical material of their own.

These patterns should be treated as high-confidence defaults, not as absolute rules. The user may always override them by providing newer transcripts that contradict an older pattern.

---

## What This Skill Does Not Do

- It does not proofread for grammar or spelling.
- It does not replace the advisor's judgment.
- It does not access external files or databases — all source material must be provided in the prompt.
- It does not process audio — transcripts must already be converted to text before input.
- It does not guarantee the advisor will not push back on a "ready to send" judgment. The goal is to reduce the probability of unnecessary revision requests, not eliminate it.

---

## Source Transcript Coverage

The Known Advisor Patterns section was derived from systematic analysis of 40+ meeting transcripts and chat logs spanning multiple years of lab interactions. Each pattern was required to appear in at least two distinct sessions before being included. Patterns with three or more supporting instances are rated high confidence.

The original transcripts are not part of this public repository. They contain private conversations and are not distributed with this skill.

---

## Design Principle: Advisor-Specific Over Generic

The skill is designed to give advisor-specific feedback, not generic writing feedback. Generic feedback ("use more transitions," "be concise," "support your claims") is already widely available. The value of this skill is that it surfaces patterns specific to how Dr. Tang actually evaluates writing — patterns derived from real interactions, not from style guides.

When evidence is thin or absent, the skill should say so, rather than substituting generic advice as if it were advisor-derived.
