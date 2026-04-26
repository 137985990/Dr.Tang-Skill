# Sample Draft Input

This file shows what a draft input looks like when using **Mode 2: Draft Review** or **Mode 3: Final Send Check**.

Paste your draft into the prompt along with the transcripts (for Mode 2) or alone (for Mode 3).

---

## Example: Introduction Paragraph (Before Review)

The following is a representative example of the kind of draft that commonly surfaces problems when reviewed against Dr. Tang's standards.

---

**Draft text:**

> Fatigue detection has become increasingly important due to the development of wearable sensors. Multi-modal approaches using EEG, ECG, and other physiological signals have shown strong performance in controlled laboratory settings. However, sensor noise, battery limitations, missing segments, and individual channel differences make data collection challenging in real-world environments. The resulting data are richer but also noisier, making high-quality acquisition difficult. Most existing approaches treat fatigue detection as a multivariate time-series learning problem and rely on general-purpose temporal encoders to capture temporal structure and cross-channel dependency.

---

## What Mode 2 Would Flag in This Draft

**Top risks:**

1. **No central thought per paragraph.** This paragraph lists several facts (sensor noise, battery issues, missing segments) but does not deliver a single central argument. Dr. Tang's expectation: every paragraph must give the reader "一句忠心思想."

2. **Overgeneralization.** "Battery limitations" is attributed to sensors broadly. Not all sensors have battery problems — some generate power from motion or heartbeat. This claim will be challenged by reviewers who can cite counterexamples.

3. **"Richer but also noisier" is contradictory without explanation.** "Richer" implies more information; "noisier" implies less usable. The relationship between these two properties is not explained. Dr. Tang's expectation: don't say things that require the reader to resolve the contradiction themselves.

4. **Missing urgency.** The paragraph states facts but does not frame the problem as urgent or unsolved. Dr. Tang expects the first paragraph to establish why practical deployment matters — not just that it is difficult.

**Must-fix before sending:**
- Remove "battery limitations" or scope it carefully with citations
- Replace the list-of-facts structure with a single argument
- Add a closing sentence establishing urgency: why does it matter that practical deployment remains unsolved?

---

## How to Provide Your Own Draft

Paste your draft directly in the prompt. Include the full section or passage — partial drafts reduce review quality. If you have a prior advisor profile, include it. If not, the Known Dr. Tang Patterns in `SKILL.md` will be applied automatically.
