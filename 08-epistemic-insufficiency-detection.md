# Epistemic Insufficiency Detection in Agentic AI

**Status: Open research idea / concept note.**

> This note presents a proposed failure mode, mechanism, or research question for further investigation. It is **not presented as a completed empirical paper or as an experimentally established theory**. Where prior research or pilot observations are discussed, they motivate the idea; the broader claims remain hypotheses to be tested, refined, or falsified.

## Knowing When the Available State Is Not Enough

**Rakesh Rajan (Rakesh OSS)**  

**Status: Open research idea / concept note.**

> This note presents a proposed failure mode, mechanism, or research question for further investigation. It is **not presented as a completed empirical paper or as an experimentally established theory**. Where prior research or pilot observations are discussed, they motivate the idea; the broader claims remain hypotheses to be tested, refined, or falsified.

## Research idea summary
Agentic AI systems are increasingly expected to act under incomplete information. Adjacent research already addresses uncertainty estimation, selective prediction, and abstention: **Don’t Hallucinate, Abstain** studies knowledge-gap detection, **AgentAbstain** evaluates whether tool-using agents know when not to act, and the broader abstention literature studies calibrated refusal under uncertainty. EID does not claim that abstention or uncertainty estimation are new.

This research idea proposes the narrower safety requirement **Epistemic Insufficiency Detection (EID)**: before committing to an interpretation, plan, or action, an agent should determine whether the information available is sufficient to justify constructing the operative state on which that commitment depends. Failure to do so can cause missing context to be replaced by learned priors, producing a coherent but unsupported state model that then drives action.

---

## 1. The Problem

Agentic systems rarely possess complete information.

They may face:

- missing observations;
- incomplete retrieval;
- ambiguous instructions;
- conflicting evidence;
- unknown dependencies;
- unresolved chronology;
- uncertain authority relationships.

The central safety question is therefore not merely:

> What is the most likely interpretation?

It is first:

> **Is there enough information to justify choosing an interpretation at all?**

Let available information be \(E\), and let \(H\) be an operative hypothesis or state model.

A system should commit to \(H\) only when:

\[
E \geq E_{\min}(H,A),
\]

where \(E_{\min}\) is the information required to justify the hypothesis given the consequence of the contemplated action \(A\).

When this condition is not satisfied, the system is in a state of **epistemic insufficiency**.

## 2. Distinguishing Insufficiency from Uncertainty

Uncertainty and insufficiency are related but different.

A model may say:

\[
P(H_1)=0.55,\qquad P(H_2)=0.45.
\]

That expresses uncertainty between known alternatives.

Epistemic insufficiency asks a deeper question:

> Are the available alternatives themselves justified by the evidence?

The agent may be choosing between \(H_1\) and \(H_2\) when the correct response is:

\[
H_3=\text{insufficient state information}.
\]

The safety failure occurs when the model is forced, implicitly or explicitly, to choose a substantive interpretation despite lacking the context needed to support one.

## 3. Prior Substitution

When information is incomplete, an LLM does not operate in an empty space.

It has learned statistical priors from training.

Thus:

\[
\text{missing context}
\]

may become:

\[
\text{missing context}
+
\text{learned prior}
\rightarrow
\text{plausible completion}.
\]

This is useful for ordinary language generation.

It can be dangerous for agentic state construction.

The system may silently replace unknown facts with what usually happens in similar situations.

The resulting representation can be fluent, coherent, and wrong.

I call this **prior substitution**:

> the replacement of unavailable task-specific information by learned statistically typical information without sufficiently preserving the distinction between known and assumed state.

## 4. Why Abstention Alone Is Not Enough

Recent research has shown that LLMs often fail to abstain when uncertain, including in tool-using agent environments. Other work has proposed uncertainty-aware abstention and explicit rejection mechanisms.

EID addresses a related but earlier point in the chain.

An agent should not merely ask:

> Am I confident enough to execute this action?

It should ask:

> **Was the state on which this action depends sufficiently determined in the first place?**

The distinction is:

\[
\text{state construction}
\rightarrow
\text{sufficiency check}
\rightarrow
\text{planning}
\rightarrow
\text{action}.
\]

If the sufficiency check occurs only after planning, the agent may already have hardened an unsupported interpretation into its operative state.

## 5. Agentic Failure Chain

Failure to detect insufficiency can initiate several downstream failures:

\[
\text{insufficient information}
\rightarrow
\text{prior substitution}
\rightarrow
\text{premature state commitment}
\rightarrow
\text{competent action}
\rightarrow
\text{environmental change}.
\]

The altered environment may then generate observations that appear to support the original assumption.

Thus:

\[
\text{epistemic insufficiency}
\rightarrow
\text{state-model divergence}
\rightarrow
\text{recursive amplification}.
\]

EID therefore operates upstream of several broader agentic safety problems.

## 6. Action Consequence Should Change the Threshold

Not every uncertainty requires abstention.

If an action is cheap and reversible, an agent can sometimes act while uncertain.

If an action is consequential or irreversible, the evidence threshold should rise.

Let action cost be \(C(A)\) and reversibility be \(R(A)\).

Then the required evidence threshold should approximately satisfy:

\[
E_{\min}=f(C(A),1-R(A)).
\]

A low-consequence search query may require little certainty.

A financial transfer, deletion, external communication, account restriction, or irreversible deployment should require substantially more.

EID is therefore not a universal instruction to refuse action.

It is a requirement to match **epistemic sufficiency to action consequence**.

## 7. What an Agent Should Detect

Before consequential commitment, an agent should identify:

1. **Missing state** — what relevant facts are unknown?
2. **Missing context** — what relationships or background conditions are required to interpret the available facts?
3. **Unresolved alternatives** — what materially different state models remain plausible?
4. **Retrieval incompleteness** — could relevant information exist but simply not have been retrieved?
5. **Authority ambiguity** — is it clear which instruction, permission, or revision governs?
6. **Sequence ambiguity** — is the ordering of relevant events established?
7. **Evidence dependence** — are apparently separate observations actually derived from the same source?
8. **Action sensitivity** — would choosing the wrong state produce significant or irreversible consequences?

If one of these materially affects the decision, the agent should gather more information, preserve multiple hypotheses, or abstain from irreversible action.

## 8. Predictions

The theory makes several testable predictions.

**P1.** Agents explicitly required to assess information sufficiency before interpretation will commit less often to unsupported state models.

**P2.** Sufficiency checks will reduce errors not corrected by ordinary confidence calibration.

**P3.** Agents will substitute learned priors more frequently when contextual information is sparse but semantically suggestive.

**P4.** High-capability agents without EID may create larger downstream errors because they act more effectively on prematurely selected states.

**P5.** Making missing information explicit should improve performance more than simply instructing the model to “be cautious.”

**P6.** Requiring agents to state what additional observation would discriminate among competing hypotheses should reduce premature commitment.

## 9. Relation to Prior Research

Research on selective prediction, hallucination reduction, uncertainty estimation, and abstention has already established that models should sometimes decline to answer or act. Recent agentic work directly evaluates whether tool-using agents know when not to act and finds substantial remaining weaknesses.

EID does not claim that abstention is new.

Its proposed contribution is to move the safety decision upstream:

\[
\boxed{\text{Do I know enough to construct this state?}}
\]

before:

\[
\boxed{\text{Am I confident enough to act on it?}}
\]

This distinction matters because confidence can be high after an unsupported state has already been constructed.

## 10. Design Requirement

Agentic systems should maintain an explicit **insufficiency state** rather than forcing every situation into a substantive interpretation.

The operative state space should therefore include:

\[
\{S_1,S_2,\ldots,S_n,S_{?}\},
\]

where:

\[
S_{?}=\text{insufficient information to determine operative state}.
\]

That state should trigger one of three behaviours:

\[
\text{retrieve more}
\]

\[
\text{ask for clarification}
\]

or

\[
\text{abstain from consequential action}.
\]

This prevents statistical completion from masquerading as factual state reconstruction.

## 11. Conclusion

An autonomous system cannot safely act simply because it can generate a plausible interpretation.

Before selecting a state model, it must determine whether the available information is sufficient to justify one.

The core failure chain is:

\[
\boxed{
\text{insufficient information}
\rightarrow
\text{prior substitution}
\rightarrow
\text{premature commitment}
\rightarrow
\text{wrong state model}
\rightarrow
\text{wrong action}
}
\]

The central safety principle is therefore:

> **Before asking whether an agent is right, ask whether it had enough information to be right at all.**

Epistemic Insufficiency Detection should be treated as an upstream safety property of autonomous systems, alongside state fidelity, sequence integrity, provenance tracking, and action control.

## Research status and next steps

This idea is offered for further thought and empirical development. Its value depends on whether controlled tests can distinguish the proposed failure from adjacent explanations, reproduce it across models and tasks, and identify conditions under which it weakens or disappears. Negative results, narrower boundary conditions, or evidence that an existing framework already explains the effect would all be informative.

## References

Feng, S., Shi, W., Wang, Y., Ding, W., Balachandran, V., & Tsvetkov, Y. (2024). *Don’t Hallucinate, Abstain: Identifying LLM Knowledge Gaps via Multi-LLM Collaboration*. ACL 2024.

Machcha, S., Yerra, S., Gupta, S., Sahoo, A., Sultana, S., Yu, H., & Yao, Z. (2026). *Knowing When to Abstain: Medical LLMs Under Clinical Uncertainty*. EACL 2026.

Liu, X., Zhang, Y. E., Kasprova, V., et al. (2026). *AgentAbstain: Do LLM Agents Know When Not to Act?*

Nguyen, V., Xu, Z., Chan, J., et al. (2026). *The Commit-Abstain Circuit: Why Language Models Hallucinate Instead of Abstaining*.

---

*Working paper. The proposed contribution is the distinction between uncertainty about an answer and insufficiency of the information state required to justify constructing an operative agentic state.*
