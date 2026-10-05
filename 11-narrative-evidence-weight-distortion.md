# Narrative Evidence Weight Distortion in Large Language Models
## When Correct Evidence Receives the Wrong Inferential Importance

**Rakesh Rajan (Rakesh OSS)**

**Status: Open research idea / concept note.**

> This note proposes a possible failure mode for further investigation. It is **not presented as a completed empirical paper or an experimentally established theory**. The concepts below are hypotheses intended to be tested, narrowed, merged with adjacent work, or rejected.

## Research idea summary

A language model may retain the relevant facts of a narrative and still reach a distorted interpretation because it assigns the wrong **relative importance** to different kinds of evidence.

This note calls the proposed failure **Narrative Evidence Weight Distortion (NEWD)**.

The idea is narrower than claiming that models simply forget evidence or misunderstand narratives. A model may correctly retrieve events, preserve their chronology, identify the speakers, and still over-weight one conspicuous statement while under-weighting a repeated behavioural pattern, a change from baseline, source asymmetry, or culturally constrained behaviour.

The proposed mechanism is:

[
oxed{
	ext{correct evidence}
+
	ext{distorted relative weighting}
ightarrow
	ext{distorted interpretation}
}
]

A related hypothesis, **Training-Induced Narrative Weight Priors (TINWP)**, asks whether training and post-training create default preferences for particular evidence classes—for example, explicit verbal statements over distributed behavioural evidence.

Both ideas require empirical testing.

## 1. The basic problem

Complex human interpretation rarely depends on one decisive sentence.

Evidence may include:

- explicit statements;
- repeated behaviour;
- changes from prior baseline;
- who initiates or withdraws;
- chronology;
- actions carrying cost or inconvenience;
- source reliability;
- private versus public behaviour;
- consistency across events;
- cultural constraints on direct expression;
- narrator-accessible versus externally observable information.

A model may retain all of these while still giving them inappropriate inferential weights.

Let a narrative contain evidence:

[
E={e_1,e_2,ldots,e_n}.
]

An interpretation (H) depends not only on whether each item is present, but on its effective contribution:

[
I(H)=f(w_1e_1,w_2e_2,ldots,w_ne_n).
]

Let (w_i^*) denote a contextually appropriate weight and (hat{w}_i) the model's effective weight.

The proposed distortion occurs when:

[
hat{w}_i 
eq w_i^*
]

for evidence important enough to change the interpretation.

The formula is schematic rather than an established quantitative model.

## 2. Why this is different from retrieval failure

Suppose a model correctly recalls:

1. a person repeatedly initiated contact;
2. the behaviour differed from that person's previous baseline;
3. several actions involved inconvenience or cost;
4. one later statement verbally minimized the relationship.

A retrieval failure would omit one or more of these observations.

NEWD instead predicts a different outcome: the model can reproduce all four accurately but allow the explicit verbal statement to dominate the other evidence automatically.

The problem would therefore lie in **weighting**, not memory.

That distinction is testable.

## 3. Candidate evidence classes

A useful experiment could separate evidence into classes such as:

### Explicit linguistic evidence
Direct statements, denials, declarations, labels, or explanations.

### Behavioural evidence
Repeated actions, initiation, avoidance, persistence, practical effort, or changes in routine.

### Baseline-change evidence
How behaviour differs from the actor's own prior pattern rather than from a population average.

### Sequential evidence
What happened before or after what, and which events could plausibly be responses to earlier events.

### Source evidence
Whether a claim comes from direct observation, first-person narration, hearsay, inference, or an interested narrator.

### Costly-action evidence
Actions involving time, effort, inconvenience, reputational exposure, or other costs.

### Cultural evidence
Context in which direct verbal expression may be encouraged, discouraged, or socially constrained.

The research question is not whether any class should always dominate. It is whether models apply **context-sensitive** weighting or rely on relatively fixed priors.

## 4. Training-Induced Narrative Weight Priors

TINWP is the hypothesis that systematic patterns in training or post-training data may create default preferences among evidence classes.

For example, a model might tend to privilege:

[
	ext{explicit statement}
>
	ext{distributed behavioural pattern}
]

even in cases where a human evaluator judges the behavioural pattern more diagnostic.

Other possible priors include:

[
	ext{recent evidence} > 	ext{earlier repeated evidence}
]

or:

[
	ext{salient phrase} > 	ext{low-salience pattern}
]

or:

[
	ext{narrator assertion} > 	ext{externally observable contradiction}.
]

These are hypotheses, not established properties.

## 5. Proposed experiments

The central experiment should hold the underlying evidence constant while changing its **presentation class**.

### Experiment A — Explicit statement versus repeated behaviour

Construct matched narratives containing:

- several repeated behavioural indicators pointing toward hypothesis (H_1);
- one explicit statement pointing toward (H_2).

Create counterbalanced versions in which the behavioural evidence and explicit statement exchange directions.

Ask models and human participants to estimate the relative support for (H_1) and (H_2).

If models systematically follow the explicit statement more strongly than human baselines despite equivalent evidence structure, that would support a weighting distortion.

### Experiment B — Baseline change

Present identical behaviour under two histories:

- condition 1: the behaviour is normal for the actor;
- condition 2: the behaviour is a large departure from the actor's baseline.

A context-sensitive interpreter should weight the same act differently across the two conditions.

### Experiment C — Cultural constraint

Keep behaviour constant while varying whether direct verbal expression is culturally easy or socially constrained.

The question is whether the model merely recognizes the cultural information when asked, or actually allows it to alter the weight assigned to observed behaviour.

### Experiment D — Salience manipulation

Hold evidentiary value constant while varying:

- vividness;
- recency;
- wording intensity;
- narrative position.

This could test whether rhetorical salience substitutes for evidentiary importance.

### Experiment E — Structured reweighting

Compare ordinary prompting with an instruction that forces the model to list evidence by class before interpreting it.

If the interpretation changes substantially after explicit evidence accounting, that would suggest the initial weighting was unstable rather than evidence-limited.

## 6. What would count against the idea

NEWD would be weakened if controlled tests show that models:

- weight behavioural, linguistic, sequential, source, and cultural evidence at least as context-sensitively as human baselines;
- show no systematic preference for explicit or salient evidence after controlling for evidentiary strength;
- remain stable under counterbalancing of evidence classes;
- gain little from structured evidence accounting;
- or are better explained by ordinary retrieval, chronology, or pragmatic-understanding failures.

TINWP would be weakened if any observed asymmetry disappears across model families, training regimes, or neutral presentation formats.

## 7. Why the idea may matter

For ordinary conversation, incorrect weighting may produce a bad interpretation.

For an agentic system, the consequences can be operational.

A model may have all the correct evidence in context yet construct the wrong operative state because one evidence class dominates inappropriately. Subsequent planning can then be coherent relative to that distorted state.

The proposed chain is:

[
	ext{evidence retained}
ightarrow
	ext{weights distorted}
ightarrow
	ext{wrong interpretation}
ightarrow
	ext{wrong operative state}
ightarrow
	ext{competent but inappropriate action}.
]

This would distinguish NEWD from failures caused primarily by missing information.

## 8. Relationship to the wider research-idea series

NEWD sits between several other proposed ideas in this collection.

- **Sequence Integrity** asks whether order is preserved.
- **Relational Topology Loss** asks whether relations such as attribution, conditionality, certainty, and scope are preserved.
- **Evidentiary Threshold Distortion** asks whether the action threshold matches the evidence.
- **Agentic State–Model Divergence** concerns the downstream gap between governing reality and the agent's operative representation.

NEWD asks a different question:

> **What if the evidence, order, and relations are all present, but the model gives the wrong pieces of evidence the wrong amount of influence?**

That distinction is the main reason the idea is worth testing separately.

## 9. Open questions

The important unresolved questions are empirical:

- Do stable evidence-class weighting biases exist across model families?
- Are they produced mainly by pretraining, post-training, prompting, or inference-time heuristics?
- Do the biases persist when narrative salience is controlled?
- Are human judgments actually more calibrated, or merely differently biased?
- Can structured evidence accounting reduce the effect?
- Which domains are most vulnerable?
- Does distorted weighting measurably propagate into agentic action?

Until such questions are tested, NEWD and TINWP should be treated as **research hypotheses**, not established mechanisms.

## Research status and next steps

This concept is offered for further thought and experimental development. Its value depends on whether controlled studies can distinguish weighting errors from retrieval, chronology, pragmatic, and source-attribution failures. Results showing narrow boundary conditions, alternative explanations, or no reproducible effect would be useful outcomes rather than failures of the research program.
