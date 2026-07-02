# U-GAT Manuscript Advisor Rules

Use this reference only for the U-GAT / fatigue detection manuscript or closely related drafts about mask-conditioned temporal imputation over aligned windows. Treat these as project-specific constraints, not universal Dr. Tang preferences.

## Revision Principle

Prioritize conceptual clarity over decorative sophistication. A high-level term is acceptable only when it is still explainable in one plain sentence.

Before editing, identify:

- What exact problem the paragraph is solving.
- Whether each new term can be explained in ordinary language.
- Whether the wording matches the actual experimental protocol.
- Whether the text claims more than the evidence supports.
- Whether the change touches advisor-provided text; preserve it unless there is a clear grammar or technical error.

## Core Problem Line

Keep the paper as a cross-domain heterogeneous sensing and imputation paper, not as a source-target transfer paper.

Preferred macro line:

`heterogeneous setups -> availability mask -> preserve observed modalities/signals -> impute unavailable parts -> support fatigue classification`

Do not make `source` / `target` the main formulation. Those terms may appear in related work background when discussing prior transfer learning, but the present method should be framed around domains, setups, masks, aligned temporal windows, and task-oriented imputation.

## Terminology Rules

Prefer:

- `impute`, `imputed values`, `imputation model`
- `mask-conditioned temporal imputation over aligned windows`
- `available / unavailable modalities`
- `fatigue classification`
- `domain` when referring to cross-domain setup differences

Avoid or replace:

- `generate`, `generated`, `generator` when it could imply creating real physiological measurements.
- `setup-conditioned window completion` because the condition comes from the availability mask, not the window itself.
- `source` / `target` as the main paper framing.
- Over-specific phrases such as `three setups` when the claim should cover `all considered setups`.
- Strong result words such as `strongest`, `consistently improves`, or `proves` unless the protocol directly supports them.

If the advisor has pushed for consistent `modality` wording, use `modality` in conceptual prose. Use `signal`, `channel`, or `column` only when an implementation detail requires that level of precision.

## Method Anchors

For U-GAT-style text, keep these anchors stable:

- The sample unit is a fixed-length temporal window.
- The aligned input has shape `T x C`.
- Rows are time steps.
- Columns are aligned input positions.
- GAT graph nodes are time steps, not sensors or channels.
- The availability mask tells the model which modalities/signals are available or unavailable.
- Imputed values are task-oriented inputs for fatigue classification, not recovered ground-truth physiological measurements.
- Auxiliary classification feedback is internal to imputation-model training.
- Downstream classifier evaluation is separate from auxiliary feedback.
- `classification-guided` or `auxiliary feedback` means guidance for imputation training, not joint training with the final downstream classifier unless the implementation truly does that.

When graph attention is mentioned, state the mechanism cleanly: graph attention models temporal relations among window time steps; cross-domain modality handling comes from the aligned representation and availability mask, not from treating sensors as graph nodes.

## Experiment Protocol Anchors

Claims must match the implemented protocol:

- Data are sampled at 32 Hz if that is the active protocol.
- Each sample is a fixed `T x C` temporal window.
- The active split is a merged individual-window split if that is what was used.
- Do not imply subject-level or session-level generalization unless the split truly enforces it.
- Imputed outputs are fixed before downstream classifier training when that is what was done.
- If standard deviations mainly come from downstream classifier seeds, say so.
- Do not imply every imputation model was fully retrained multiple times unless it was.
- If robustness uses a fixed seed, call it fixed-seed sensitivity or explicitly state the limitation.

For result interpretation, prefer guarded language:

- `higher mean values appear in ...`
- `the effect depends on the setting`
- `the results suggest ... under this protocol`
- `the comparison supports ... rather than proving ...`

## Table IV / Label-Guided Distinction

Do not mix two different mechanisms:

- Auxiliary classification feedback is an internal training signal for U-GAT.
- Table IV `Label-guided` refers to an external imputation-model output comparison if that is how the experiment is set up.

When reviewing or rewriting this part, explicitly check whether the paragraph incorrectly treats these as the same thing.

## Collaboration Rules For This Manuscript

When asked to revise the manuscript, especially after advisor edits:

- Present substantive wording changes in Chinese first.
- Explain why each change is needed.
- Wait for user approval before editing paper text when the user asks to review proposed changes first.
- Do not change formulas unless explicitly requested.
- Do not delete or alter table data.
- Protect advisor red edits; only modify them for clear grammar or technical errors.
- When requested, mark new author-side changes visibly, using the color/comment convention specified by the user.
- After editing, compile or otherwise verify before claiming completion.

## Common Failure Modes

| Failure mode | Correction |
|---|---|
| Treating imputation as recovery of true physiological measurements | Say imputed values are task-oriented inputs for fatigue classification. |
| Calling the method setup-conditioned | Say mask-conditioned if the mask is the actual condition signal. |
| Writing the main story as source-target transfer | Reframe as cross-domain heterogeneous sensing with structural modality absence. |
| Saying the graph models sensor/channel relations | Say graph nodes are time steps; channel handling happens through aligned columns and masks. |
| Claiming broad robustness from fixed-seed checks | Call it fixed-seed sensitivity or state the limitation. |
| Letting table labels imply a different protocol | Clarify the surrounding text without changing table data unless the user explicitly approves. |
