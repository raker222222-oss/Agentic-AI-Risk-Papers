# Language-Mediated State Reconstruction in Agentic AI
## A Failure Theory of Probabilistic World-State Recovery

**Rakesh Rajan (Rakesh OSS)**  
**Working paper**

## Abstract

Human communication usually begins with a rich underlying state—perception, chronology, intention, social context, uncertainty, and embodied experience—and compresses that state into language. Language models often face the reverse problem: they receive the compressed linguistic representation and must reconstruct the state that could have produced it.

Because language is information-reducing, this inverse reconstruction is generally underdetermined. Multiple underlying states may be compatible with the same text. A language model therefore relies on learned statistical priors to select among possible reconstructions.

This paper proposes that several apparently separate LLM and agentic failure modes can be understood as downstream consequences of that architectural condition. When linguistic evidence is insufficient, the model may substitute a statistically likely state for an epistemically warranted one; once selected, that state can reshape evidence weighting, anomaly status, provenance, authority, sequence, and uncertainty. In an agentic system, the resulting state model can then drive action and generate feedback that reinforces the original reconstruction.

The central safety requirement is therefore not merely better language understanding, but **epistemically constrained state reconstruction**.

---

## 1. Language as a Compressed Representation of State

Let \(S\) represent the underlying human or environmental state and \(L\) the linguistic representation produced from it:

\[
L=\Phi(S).
\]

The mapping \(\Phi\) is highly compressive. Language rarely preserves every relevant feature of the originating state.

Consequently:

\[
S_1\neq S_2
\]

may still produce:

\[
\Phi(S_1)\approx \Phi(S_2).
\]

Given only \(L\), the inverse problem is therefore non-unique:

\[
\Phi^{-1}(L)=\{S_1,S_2,\ldots,S_n\}.
\]

An LLM must select or construct an operative state:

\[
\hat S=\arg\max_S P(S\mid L).
\]

Learned priors are therefore not peripheral to interpretation. They participate directly in state construction.

---

## 2. The Linguistic Inverse Problem

The architectural asymmetry is:

\[
\text{state}\rightarrow\text{language}
\]

for the original communicator, but often:

\[
\text{language}\rightarrow\text{reconstructed state}
\]

for the language model.

This reversal matters because information discarded during the first mapping cannot be recovered directly during the second.

The model must infer missing structure.

A safe system should preserve the distinction between:

\[
\text{observed}
\]

\[
\text{explicitly constrained}
\]

\[
\text{inferred}
\]

and

\[
\text{assumed from prior}.
\]

Failure occurs when these categories collapse and the statistically preferred reconstruction becomes the operative state without adequate epistemic qualification.

---

## 3. Prior-Driven State Selection

Let \(E\) denote the available evidence and \(P(S)\) the learned prior over possible states.

Then:

\[
P(S\mid E)\propto P(E\mid S)P(S).
\]

Using priors is not itself a failure. The problem arises when a strong prior overrides evidence that should constrain the reconstruction.

This produces **prior-dominant state construction**:

\[
\text{insufficient or ambiguous evidence}
\rightarrow
\text{high-probability prior}
\rightarrow
\hat S.
\]

A familiar interpretation may therefore require little additional evidence, while a less typical but contextually valid alternative faces a much higher burden.

What appears as evidentiary inconsistency may thus originate earlier, during state selection.

---

## 4. Context as Constraint, Not Merely Signal

Additional context should reduce the set of admissible states:

\[
\Phi^{-1}(L,C)\subseteq\Phi^{-1}(L).
\]

But this requires the model to treat some contextual elements as binding constraints rather than merely additional statistical features.

Chronology, authority, explicit clarification, provenance, and contradiction can restrict which reconstructions are admissible.

If they are instead treated as soft semantic cues, a dominant learned prior may reinterpret them rather than be constrained by them.

Thus the failure is not always lack of context.

It may be:

> **failure to grant available context sufficient epistemic authority.**

---

## 5. From Reconstruction to Coherence Preservation

Once an operative state \(\hat S\) is selected, subsequent evidence is interpreted relative to it.

A conservative update would test new evidence against the current state and reopen the hypothesis when necessary.

But a model may instead preserve coherence by changing the epistemic role of new or retained information.

This produces **Coherence-Dominant Epistemic Reconstruction (CDER)**:

\[
\text{dominant reconstructed state}
\rightarrow
\text{evidence reweighting}
\rightarrow
\text{anomaly downgrading}
\rightarrow
\text{inference hardening}
\rightarrow
\text{coherent narrative}.
\]

The underlying facts may remain present while their epistemic relationships change.

That is **Relational Epistemic Instability (REI)**.

---

## 6. A Unified Failure Chain

The proposed architecture is:

\[
\boxed{
\text{lossy linguistic representation}
\rightarrow
\text{underdetermined state reconstruction}
\rightarrow
\text{prior-driven selection}
\rightarrow
\text{coherence preservation}
\rightarrow
\text{epistemic relation distortion}
\rightarrow
\text{wrong operative state}
}
\]

For an agentic system:

\[
\boxed{
\text{wrong operative state}
\rightarrow
\text{competent action}
\rightarrow
\text{environmental change}
\rightarrow
\text{new evidence}
\rightarrow
\text{possible reinforcement}
}
\]

The failure therefore begins before planning.

The agent may reason perfectly relative to an incorrectly reconstructed state.

---

## 7. Relation to the Existing Failure Framework

This architecture provides an upstream explanation for several previously identified failure modes.

**Epistemic Insufficiency Detection:** the system fails to recognize that the available language does not uniquely determine the state.

**Interpretive Displacement:** a learned prior supplies a plausible but incorrect interpretation.

**Sequence Integrity Failure:** chronology is retained as text but not treated as a binding constraint on reconstruction.

**Evidentiary Threshold Distortion:** evidence compatible with the selected state receives a lower practical threshold than evidence challenging it.

**Open-World Retrieval Failure:** missing external state is silently replaced by a plausible internal completion.

**Relational Epistemic Instability:** the system preserves content while changing provenance, uncertainty, authority, anomaly status, or observation/inference status.

**Agentic State-Model Divergence:** the reconstructed operative state differs materially from the governing state.

**Recursive Amplification:** action based on that state changes the future evidence stream and may strengthen the original error.

**Rogue Without Will:** none of these failures requires independent malicious intent.

---

## 8. Relation to Prior Research

Prior work already establishes several important components of this account.

Pragmatics has long treated linguistic meaning as underdetermined by linguistic form alone. Rational Speech Act models formalize interpretation as probabilistic inference over latent speaker states. Symbol-grounding research examines the relationship between linguistic symbols and non-linguistic experience. Recent work on LLM world models argues that human language contains compressed traces of collective grounded experience from which models can reconstruct useful latent structure. Agentic research increasingly emphasizes explicit belief-state maintenance under partial observability.

The proposed contribution here is narrower:

> **If language-mediated state reconstruction is inherently underdetermined, then learned priors do not merely help interpretation; they can become structural substitutes for missing state. The resulting reconstruction can then alter epistemic relations, produce operative state divergence, and enter recursive agentic feedback.**

The theory therefore focuses on the safety consequences of language-mediated state reconstruction rather than on whether language models possess world models or grounding in a philosophical sense.

---

## 9. Testable Predictions

The theory predicts that:

1. models will make larger state-reconstruction errors when linguistically plausible priors conflict with explicit but weakly represented constraints;
2. preserving explicit distinctions among observation, inference, assumption, and retrieval will reduce reconstruction errors;
3. models will perform better when chronology, authority, provenance, and uncertainty are represented structurally rather than embedded only in prose;
4. ambiguous inputs will produce premature state commitment unless an explicit “insufficient information” state is available;
5. strong initial reconstructions will cause later contradictory evidence to be reweighted rather than trigger full state reopening;
6. agents that verify reconstructed state before planning will outperform otherwise identical agents that plan directly from free-form linguistic context.

---

## 10. Safety Principle

The design implication is:

\[
\boxed{
\text{language}
\rightarrow
\text{candidate states}
\rightarrow
\text{epistemic validation}
\rightarrow
\text{operative state}
\rightarrow
\text{plan}
\rightarrow
\text{act}
}
\]

rather than:

\[
\text{language}
\rightarrow
\text{most plausible state}
\rightarrow
\text{act}.
\]

A safe agent should not ask only:

> What state is most likely given this language?

It should also ask:

> Which parts of this state are observed, constrained, inferred, assumed, unresolved, or missing?

---

## 11. Conclusion

Language is a compressed representation of state.

Recovering state from language is therefore generally an inverse problem with multiple admissible solutions.

Large language models resolve that ambiguity using learned statistical structure. This is a source of their power, but also a source of systematic risk.

When statistical plausibility substitutes for epistemically constrained reconstruction, a model can construct the wrong state while retaining the right words. Once that state becomes operative, downstream reasoning can be coherent, competent, and dangerous.

The central proposition is therefore:

\[
\boxed{
\text{probable reconstruction}
\neq
\text{epistemically warranted reconstruction}.
}
\]

Agentic AI safety should treat the distinction between the two as a first-class architectural requirement.

---

*Working paper. The proposed contribution is not that language is compressed, probabilistic interpretation exists, or belief-state estimation is necessary. It is the proposed failure chain connecting underdetermined language-to-state reconstruction, prior substitution, epistemic relation distortion, operative state divergence, and recursive agentic action.*