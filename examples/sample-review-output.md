# Sample Review Output

This file shows what a full **Mode 2: Draft Review** output looks like, demonstrating the two-stage logic: advisor profile first, then draft review.

---

## Input

**Source material:** Three meeting transcripts (see `sample-transcript-input.md`)
**Draft:** Introduction paragraph (see `sample-draft-input.md`)

---

## Stage 1: Advisor Priority Profile (Mode 1 output)

### Core Expectations
- Every paragraph must deliver one clear central thought
- Before sending: read the full document front-to-back; two passes is likely not enough
- Strong claims require citations — don't assert what is or isn't true without evidence

### Common Dissatisfaction Triggers
- Sentences that are individually correct but together produce no point
- Overgeneralizations that a reviewer with one counterexample can defeat
- Logic gaps between paragraphs — the reader loses the thread

### Tone and Language Preferences
- Diplomatic framing: "has room for improvement" not "has a deficit"
- "Challenging in real-world deployment" over "impractical"
- Scope claims carefully: "many sensors" not "all sensors"

### Confidence Assessment
- **High confidence:** central thought per paragraph, read before sending, cite strong claims
- **Medium confidence:** diplomatic framing (2 instances)
- **Low confidence:** none identified in this transcript set

---

## Stage 2: Draft Review (Mode 2 output)

### Alignment with Advisor Expectations
- The draft correctly identifies that real-world deployment is a challenge area
- The mention of multi-modal approaches is appropriate for this paper's scope

### Top Risks

1. **No central thought delivered.** The paragraph lists five problems (noise, battery, missing segments, channel differences, noisy data) without arriving at a single argument. Dr. Tang will ask: "What's the one thing you want me to take from this paragraph?"

2. **Unsupported overgeneralization.** "Battery limitations" is applied to sensors broadly. Without a citation, this will be challenged. Some sensors are self-powered; some biosignal sensors have negligible power draw.

3. **No urgency established.** The paragraph describes difficulty but not why it matters that the problem is unsolved. Dr. Tang expects the first paragraph to end with a statement of urgency — not just that the challenge exists, but that its continued existence is a critical research gap.

### Must-Fix Before Sending

- [ ] Remove "battery limitations" or add a citation and scope it: "certain wearable sensors face battery constraints [REF]"
- [ ] Replace the list structure with one clear argument: what is the single problem this paragraph is establishing?
- [ ] Add a closing sentence establishing urgency: something like "Reliable fatigue detection in practical environments remains an unresolved critical research challenge."

### Suggested Improvements (Non-Blocking)

- Consider splitting the current paragraph: one paragraph on why multi-modal approaches have shown promise, and a second on why they fail in deployment. This gives each paragraph a single job.
- "The resulting data are richer but also noisier" — this contradiction needs either explanation or removal.

### Rewritten Passages

**Passage 1 — Opening claim**
- Original: "Fatigue detection has become increasingly important due to the development of wearable sensors."
- Suggested: "Fatigue detection is a safety-critical task with direct implications for accident prevention in driving, aviation, and industrial operation."
- Reason: Dr. Tang expects the first sentence to establish importance and urgency, not attribute importance to a technological development. The urgency belongs to the application domain, not the tool.

**Passage 2 — Closing**
- Original: [paragraph ends after listing challenges]
- Suggested: "Despite this progress, reliable fatigue detection in real-world deployment remains an underexplored critical challenge."
- Reason: Dr. Tang explicitly expects the first-paragraph endpoint to name the unresolved urgency that motivates the paper.

### Send Readiness

**Not ready yet.**

The paragraph does not deliver a single clear central argument and contains at least one unsupported broad claim (battery limitations). These are the two most common problems Dr. Tang flags, and both are present here. Resolve the blocking items before sending.

### Confidence and Uncertainty

- High confidence: the must-fix items are supported by patterns that appear in 3+ transcript interactions
- The specific suggested rewrites are illustrative — the advisor's own examples of good writing would be more authoritative if available
