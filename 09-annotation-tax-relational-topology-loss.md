# The Annotation Tax: Relational Topology Loss in Human–LLM Conversation

**Status: Open research idea / concept note.**

> This note proposes a way of describing and testing a possible class of conversational failures. It is **not presented as a completed empirical paper or an experimentally established theory**. RTL begins as a candidate level of analysis; the Annotation Tax is a proposed measure whose usefulness depends on empirical validation against human and model baselines.

**Rakesh Rajan (Rakesh OSS)**

## Research idea summary
Large language models can preserve the apparent propositional content of a conversation while altering the relations that determine what those propositions mean. An intuition may later be treated as fact; a conditional response may become an unconditional intention; a quotation may become the speaker's own belief; temporal order may reverse; or a qualification may cease to constrain the proposition it originally modified.

We call this class of failures **Relational Topology Loss (RTL)**: a proposed failure mode in which an LLM retains the visible informational elements of a conversation but fails to correctly use the relations among those elements that determine meaning. The relevant words, speaker labels, chronology, questions, answers, and propositions may remain available while a functional relation is omitted, misassigned, weakened, inverted, or overridden.

In simple terms: **the nodes survive, but the edges do not function correctly.**

Here, “topology” refers to the pattern of functional relations among conversational elements, not to a claim about mathematical topology or a specific internal neural representation.

RTL is proposed first as a **behavioral level of analysis**, not as a claim that epistemic, temporal, conditional, attributional, pragmatic, and discourse-structural errors arise from one computational mechanism. From model outputs alone, we cannot determine whether a relation was never represented internally, represented incorrectly, represented but unused, or represented correctly and then overridden by a stronger prior or interpretation. This distinction leads to a second concept, the **Annotation Tax**: the additional communicative work required to make such relations explicit enough for a model to preserve them reliably.

Because humans also require clarification, the meaningful quantity is the **Excess Annotation Tax**: the additional annotation required by an LLM relative to competent human interlocutors on the same material.

We propose an experimental framework that separately measures proposition retention and relation retention, perturbs one relational edge at a time, tracks degradation across intervening conversational turns, compares models with human baselines, and tests whether explicit annotation reduces relational errors. We distinguish preventive, repair, persistence, and action-oriented annotation costs.

The framework has particular implications for agentic AI. An agent need not hallucinate a new proposition to act incorrectly. It may preserve the proposition while losing a conditional, epistemic, temporal, attributional, or scope relation, reason coherently from the corrupted state, and execute an action never warranted by the original instruction.

The resulting risk is therefore not simply hallucination. It is **structurally faithful language built upon a relationally corrupted state**.

## 1. Introduction

Human conversation is not a sequence of independent propositions.

Consider:

> “I think she will leave tomorrow.”

If a system later represents this as:

> “She leaves tomorrow,”

much of the lexical content survives, but the epistemic status has changed.

Now consider:

> “I want to ask him why he did it. If he insults me, I may respond in kind.”

A summary such as:

> “You want to confront him and insult him”

preserves several content elements while deleting the conditional dependency governing the second action.

The distinction is therefore between **proposition retention** and **relation retention**.

## 2. Conversational structure as relations

Let a conversational state be represented approximately as:

G = (V, E)

where V represents propositions or discourse units and E represents relations among them.

Relevant edge types include:

- **Epistemic** — fact, belief, suspicion, intuition, possibility, uncertainty.
- **Conditional** — if, unless, only if, contingent response.
- **Temporal** — before, after, during, future, past.
- **Attributional** — who said, believed, reported, or quoted something.
- **Causal** — cause, consequence, explanation.
- **Scope** — which qualifier, negation, restriction, or modality applies to which proposition.
- **Pragmatic** — sarcasm, joking, exaggeration, rhetorical use.
- **Discourse-structural** — contrast, elaboration, correction, concession, reply and dependency.

These categories are deliberately separated. A central empirical question is whether they degrade together, independently, or in characteristic clusters.

RTL therefore begins as a **shared behavioral evaluation framework**, not as an assertion that all relational errors are generated by one hidden mechanism.

A further boundary is necessary: not every disagreement in interpretation is RTL. Human conversation is often genuinely ambiguous. RTL is the narrower case in which a relevant relation is already available in the interaction, yet the model fails to use that relation correctly when reconstructing meaning, intention, relationship state, or another human state.

The working distinction is:

**information availability ≠ relational operationalization**

## 3. Types of Relational Topology Loss

### 3.1 Edge deletion

Original:

> “If the customer fails to respond by Friday, cancel the order.”

Reconstruction:

> “Cancel the order.”

The conditional relation has vanished.

### 3.2 Edge reassignment

Original:

> “My intuition is that the meeting will be postponed.”

Later representation:

> “The meeting will be postponed.”

The epistemic state moves from intuition toward assertion.

### 3.3 Edge inversion

Original:

> “The warning came before the failure.”

Reconstruction:

> “The failure occurred before the warning.”

### 3.4 Edge misattribution

Original:

> “The analyst said the company may default.”

Reconstruction:

> “You believe the company may default.”

### 3.5 Scope loss

Original:

> “I am uncertain only about the timing.”

Reconstruction:

> “You are uncertain about the entire account.”

### 3.6 Pragmatic reassignment

Examples include sarcasm → sincerity, joke → proposal, and exaggeration → factual claim.

## 4. RTL is not ordinary forgetting

If a model forgets the whole proposition “The supplier may be late,” that is ordinary information loss.

If it later represents “The supplier is late,” the proposition survives in recognizable form while modal status changes.

The central empirical comparison is therefore **Node Retention** versus **Edge Retention**.

A model could score highly on the first and poorly on the second.

## 5. The Annotation Tax

When relational structure is not reliably inferred or preserved, users compensate:

> “This is only my intuition. I do not know this as a fact.”

> “I am not planning to attack him. I mean only that if he attacks me first, I might respond.”

> “I am being sarcastic.”

The user is effectively annotating ordinary conversation for the system.

Let AT_M(P) be the minimum annotation required for model M to preserve the intended relation of proposition P at a chosen reliability threshold. Let AT_H(P) be the equivalent requirement for competent human interlocutors.

Then:

EAT_M(P) = AT_M(P) - AT_H(P)

where EAT is the **Excess Annotation Tax**.

The testable claim is not that humans require zero annotation, but that for some conversational relations:

AT_M > AT_H.

## 6. Four forms of Annotation Tax

- **Preventive tax** — extra language supplied because misunderstanding is anticipated.
- **Repair tax** — extra language required after a misunderstanding.
- **Persistence tax** — repeated clarification required because a previously correct interpretation drifts over later turns.
- **Action tax** — additional specification required before an agent can safely act.

The **Persistence Tax** is especially important. A model may interpret a relation correctly at first and silently change it several turns later. That is not first-pass comprehension failure; it is **relational state-maintenance failure**.

## 7. Relation to prior research

The components of this problem have substantial precedents. Research on pragmatics, implicature, reference, epistemic modality, speaker commitment, event factuality, temporal ordering, discourse relations, conditionals, dialogue-state tracking, Rhetorical Structure Theory (RST), Segmented Discourse Representation Theory (SDRT), and multi-turn model degradation already establishes that conversational meaning extends beyond isolated propositions.

The paper therefore does **not** claim novelty for representing factuality, commitment, discourse relations, or pragmatic status.

The proposed contribution is narrower: to evaluate **LLM conversational degradation as divergence between intended and reconstructed relational structure across multiple turns**, and to quantify the human effort required to prevent or repair that divergence.

This framing is compatible with work on CommitmentBank-style speaker commitment, FactBank-style factuality, RST, SDRT, and recent studies of epistemic modality, temporal ordering, implicit discourse relations, pragmatic over-inference, conditional reasoning, conversational grounding, speaker attribution, multi-party dialogue comprehension, and long-context positional effects.

The narrower proposed contribution is not that discourse relations matter; that is already well established. It is that **a model may retain all relevant conversational elements and still infer the wrong human relationship, intention, or mental state because an already-present functional relation is not correctly operationalized.**

### Supporting principle: Coherence is not identification

A coherent interpretation is not necessarily the correct interpretation. Several incompatible relational states may fit the same visible evidence. Fluency and internal consistency therefore do not establish that the model has identified the underlying human state.

### Related phenomenon: Interpretive Authority Displacement

A related but separate phenomenon may occur when a model moves from offering a possible interpretation to overriding a speaker’s explicit account of their own meaning or internal state:

> “This could be interpreted as X.”

becomes:

> “You say you mean Y, but what you really feel may be X.”

This is **not** claimed here as a necessary consequence of RTL or as a wholly new theory. It overlaps with existing work on epistemic authority, algorithmic authority, testimonial injustice, and hermeneutical injustice. The narrower concern is the conversational shift from probabilistic interpretation to unwarranted confidence about another person’s internal state.

## 8. Falsifiable experimental design

The motivating examples are not evidence. The hypothesis should be tested experimentally.

### 8.1 Relation-perturbation set

Construct matched items differing in one relational property:

- fact ↔ intuition
- unconditional ↔ conditional
- speaker belief ↔ reported belief
- before ↔ after
- certain ↔ possible
- literal ↔ sarcastic
- broad scope ↔ narrow scope

Lexical variation should be minimized.

### 8.2 Delayed testing

Probe relation status immediately and again after 0, 2, 5, 10, and 20 intervening turns.

Let R_e(t) denote retention of relation type e after conversational distance t.

The key question is not merely whether the model understood the statement initially, but whether it **preserved the relation later**.

### 8.3 Neutral-fact control

Include neutral facts lacking difficult relational structure. If neutral proposition retention remains high while relation-bearing statements degrade, RTL becomes more informative than generic context loss.

### 8.4 Human baseline

Human participants should receive the same conversations. This permits direct comparison and measurement of Excess Annotation Tax rather than assuming human interpretation is perfect.

### 8.5 Annotation ladder

For each relation, test increasing explicitness: ordinary conversation, compact label, natural-language annotation, explicit exclusion, and fully specified relation. The minimum annotation needed to reach a chosen retention threshold estimates the tax.

## 9. Measuring RTL

A model's internal graph cannot be observed directly. RTL must therefore be measured through **elicited reconstruction**.

After each dialogue, ask for structured fields such as proposition, speaker, status, time, condition, scope, and source.

Classify edge errors as:

- deletion
- reassignment
- inversion
- misattribution
- scope loss

A simple metric is:

RTL = Σ(w_k E_k) / Σ(w_k N_k)

where E_k is the number of errors of edge type k, N_k the number of opportunities, and w_k an optional severity weight.

Initial experiments should report unweighted results as well. Inter-annotator agreement is necessary, especially for pragmatic edges such as irony and sarcasm.

## 10. What would weaken the hypothesis?

A strong unified RTL account would be weakened if:

1. relation errors show no pattern beyond generic forgetting;
2. relation retention is no worse than proposition retention;
3. annotation does not systematically improve preservation;
4. humans require comparable amounts of annotation;
5. different relation types behave entirely independently and respond to unrelated interventions.

The fifth result would not invalidate the framework. It would suggest that RTL is better understood as a **taxonomy of relational fragilities** than as one unified underlying mechanism.

## 11. Who pays the tax?

The burden need not fall entirely on the human.

A system could maintain an explicit relational ledger:

- Claim: event occurs tomorrow
- Source: user
- Status: intuition
- Confirmed: no
- Scope: timing

The system could also ask clarification when relation confidence is low.

This suggests a broader concept: **Topology Maintenance Cost** — the computational or communicative effort required to preserve conversational relations. That cost can be paid by the user through annotation, by the system through structured state maintenance and clarification, or jointly.

The Annotation Tax is the **human-paid component** of that cost.

## 12. Agentic systems

The distinction becomes more consequential when the model can act.

Consider:

> “If the supplier has not replied by Friday, cancel the order.”

Suppose the cancellation instruction is retained while the condition “no reply by Friday” is lost.

The agent need not hallucinate a new instruction. It can reason correctly from the corrupted representation.

Likewise:

> “I suspect this transaction may be fraudulent.”

can become:

> “This transaction is fraudulent.”

The failure chain is:

Correct utterance → Relational corruption → Incorrect conversational state → Coherent reasoning → Incorrect action.

The reasoning may be internally consistent. The state from which it begins may already be wrong.

## 13. Relation to Agentic State–Model Divergence

Relational Topology Loss can be one pathway into **Agentic State–Model Divergence (ASMD)**.

If a relational edge is deleted or reassigned during interpretation, the model's operative state diverges from the state intended by the user. Subsequent reasoning may amplify that divergence without any further interpretive error.

Thus:

RTL → ASMD

is a plausible causal pathway to investigate experimentally.

Agentic risk need not begin with malicious objectives or extraordinary hallucination. It can begin with something as small as **the loss of an “if.”**

## 14. Conclusion

An LLM may remember **what was said** while failing to preserve **how what was said relates to everything else**.

Or more compactly:

**A model can retain the conversation while losing the relationship inside the conversation.**

A possibility can become a fact. A response can become an intention. A report can become a belief. A condition can become a command. A qualifier can lose its scope.

We call this family of errors **Relational Topology Loss**.

When humans compensate by making ordinary conversational relations increasingly explicit, they incur an **Annotation Tax**.

The strongest form of the hypothesis remains empirical. The relevant experiment is not merely whether an LLM understands sarcasm, uncertainty, conditional language, or temporal sequence in isolation. It is whether the model can **preserve those relations as stable conversational state**, and how much additional language is required when it cannot.

For agentic systems, the stakes are greater. A system need not invent a false proposition to perform the wrong action. It may only need to lose the relation that made the proposition safe.

---

## Status

Independent working paper. Not peer reviewed.

## Author

**Rakesh Rajan — Rakesh OSS**

Part of the **Agentic AI Risk Papers** series.

Repository: https://github.com/raker222222-oss/Agentic-AI-Risk-Papers

DOI collection: https://doi.org/10.5281/zenodo.23040884
## Research status and next steps

The central questions remain empirical: whether the proposed relation types show measurable retention failures, whether those failures cluster, how much additional annotation models require relative to humans, and whether the framework adds explanatory value beyond existing pragmatic, discourse, temporal, and modal benchmarks.

---

## Context expansion and relational invariance

RTL also suggests a related principle: **adding context should not alter conversational relations that the added context does not bear upon.**

If a proposition's speaker, epistemic status, temporal position, conditional dependency, pragmatic function, or discourse role is already fixed, later contextual enrichment should preserve that edge unless the new material explicitly corrects or supersedes it.

Let (G(C)=(V,E_C)) represent the model's reconstructed conversational graph under context (C). For a relation (e) whose governing evidence is unchanged between (C_1) and (C_2), a desirable invariance property is:

[
ein E_{C_1}Rightarrow ein E_{C_2},
]

unless (C_2) contains information that directly revises that relation.

This yields another way to test relational robustness. Instead of asking only whether the model can recover an edge once, compare whether the same edge survives **context expansion**. A model may retain all propositions yet alter their topology as additional framing activates a different narrative.

This is especially important for discourse structure and pragmatic interpretation. Context should constrain ambiguous relations, but it should not license arbitrary reassignment of already-established ones.

The resulting evaluation question is:

> **Which relations remain invariant when context is expanded, and which are silently rewritten even though the added context does not justify the change?**

This criterion complements the Annotation Tax by testing whether users must repeatedly restate already-established relations merely to keep them stable as more context enters the conversation.
