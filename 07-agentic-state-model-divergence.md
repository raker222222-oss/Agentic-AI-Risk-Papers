# Agentic State-Model Divergence
## A General Theory of Non-Malicious AI Failure

**Rakesh Rajan (Rakesh OSS)**  
**Working paper**

## Abstract

Agentic State-Model Divergence (ASMD) proposes a unifying theory for a large class of non-malicious agentic AI failures. Prior research has established problems in long-horizon state tracking, belief representation, memory, and state externalization. ASMD extends this work by arguing that failures in task understanding, authority, evidence, and environmental representation can be treated as different forms of divergence between the agent’s operative internal state and governing reality. The danger arises when the agent then acts competently on that incorrect state, changes the environment, and potentially generates evidence that reinforces the original error.

## 1. Introduction

An autonomous AI system does not act directly on reality. It acts on a representation of reality.

Let:

\[
S_t
\]

represent the relevant state of the task or environment at time \(t\), and:

\[
\hat S_t
\]

represent the state the agent believes it is operating within.

The central proposition of **Agentic State-Model Divergence (ASMD)** is simple:

\[
\boxed{\hat S_t \neq S_t}
\]

can become a fundamental source of agentic failure even when the agent has the correct objective and reasons coherently.

The agent may retrieve information, interpret instructions, reconstruct events, evaluate evidence, plan, and use tools competently. But if those operations produce the wrong operative state, subsequent competence can increase rather than reduce the consequences of the mistake.

The resulting failure is:

\[
\text{wrong state}
\rightarrow
\text{competent reasoning}
\rightarrow
\text{wrong action}.
\]

ASMD therefore shifts part of the safety question from:

> Does the agent have the correct goal?

 to:

> Does the agent correctly understand the state in which that goal must be pursued?

## 2. Relation to Prior Research

ASMD builds on an existing body of work rather than claiming that state representation itself is a new problem.

Recent research on long-horizon agents has emphasized the need to maintain explicit belief states under partial observability. Work such as Agent-BRACE separates beliefs from actions and represents uncertainty about environment state rather than allowing an agent to collapse prematurely onto one interpretation.

Other work has shown that persistent state is increasingly externalized rather than left for the model to reconstruct repeatedly from expanding context. InfiAgent externalizes persistent task state into a file-based representation, while broader reviews describe memory and protocols as mechanisms for externalizing cognitive state and interaction structure.

State-aware runtime approaches similarly argue that long-horizon failures can arise from unstable state maintenance, memory injection, protocol drift, tool-mediated effects, and inadequate validation or rollback.

ASMD differs primarily in its proposed **level of abstraction**. It treats several apparently separate problems not merely as engineering failures of memory or runtime management, but as different routes into one safety condition:

\[
\text{operative state} \neq \text{governing state}.
\]

## 3. Four Forms of Divergence

ASMD identifies four principal forms.

### 3.1 Task-State Divergence

The agent misunderstands what task it is actually performing.

This may result from:

- incomplete retrieval;
- incorrect interpretation;
- lost sequence;
- obsolete information;
- premature assumptions;
- failure to recognize a changed objective.

The system may nevertheless produce a sophisticated plan for the wrong task.

### 3.2 Authority-Structure Divergence

Agentic tasks frequently contain hierarchical information:

- instructions;
- prohibitions;
- permissions;
- clarifications;
- exceptions;
- revisions;
- revocations.

These cannot safely be represented as an unordered collection of statements.

An agent may retain every statement while assigning operational authority to the wrong one.

For example:

\[
I_1:\text{permission granted}
\]

followed later by:

\[
I_2:\text{permission revoked}.
\]

Remembering both statements is insufficient. The operative state must represent:

\[
I_2 > I_1.
\]

If the agent instead allows a salient but subordinate statement to dominate a governing instruction, it has experienced authority-structure divergence.

### 3.3 Evidence-State Divergence

An agent must know not only what evidence exists, but what that evidence represents.

Divergence can occur when the system:

- treats absence of retrieval as evidence of absence;
- confuses inference with observation;
- loses provenance;
- treats correlated evidence as independent;
- applies inappropriate proof thresholds;
- mistakes its own earlier output for external confirmation.

A specific pathway is **epistemic laundering**: a model-generated inference is summarized, stored, retrieved, or transmitted until its original status as an inference is no longer preserved. It can then re-enter the agent's state as if it were an observed or independently verified fact. No new evidence is required; only the epistemic lineage is lost.

Thus:

\[
\text{observation}
\rightarrow
\text{model inference}
\rightarrow
\text{status/provenance loss}
\rightarrow
\text{apparent fact}.
\]

This can produce evidence-state divergence even when the proposition itself is remembered accurately.

Thus an agent may possess considerable information while holding the wrong model of the evidentiary state.

### 3.4 Environment-State Divergence

The system may form an incorrect representation of the external environment itself.

This is particularly important in long-horizon tasks and partially observable environments, where agents must infer hidden or changing state from incomplete observations. Existing research on belief-state representations directly addresses this problem.

ASMD emphasizes what follows when the incorrect estimate becomes operational.

## 4. Correct Goals Are Not Sufficient

Let the agent's goal be \(G\), and suppose the goal is correctly aligned:

\[
G=G^*.
\]

Its policy nevertheless operates on its estimated state:

\[
A_t=\pi(G,\hat S_t).
\]

Therefore:

\[
G_{\text{correct}}+\hat S_{\text{wrong}}
\rightarrow
A_{\text{wrong}}.
\]

This separates ASMD from theories requiring malicious intent, deceptive behaviour, or independently misaligned goals.

The agent can be:

- obedient;
- honest;
- competent;
- correctly motivated;

and still cause harm because it is acting inside the wrong representation of reality.

## 5. Coherent Reasoning Can Increase the Danger

Once an incorrect state model has been established, downstream reasoning may be entirely coherent.

The system can:

1. identify appropriate actions for \(\hat S_t\);
2. rank them correctly;
3. use tools effectively;
4. execute accurately;
5. explain the decision persuasively.

The reasoning may therefore be locally correct while globally wrong.

Formally:

\[
A_t=\arg\max_A U(A\mid G,\hat S_t)
\]

may be an excellent optimization procedure.

The failure occurred earlier.

This creates a counterintuitive prediction:

> Increasing planning competence does not necessarily reduce ASMD risk.

If two agents possess the same wrong state model, the more capable one may execute the resulting mistake more effectively.

## 6. Agency Turns Representation Error Into World Change

A static model produces an incorrect answer.

An agent changes the environment.

Let:

\[
S_{t+1}=T(S_t,A_t).
\]

If \(A_t\) was selected from an incorrect \(\hat S_t\), the world is now partly changed because of the original divergence.

The agent then receives new observations:

\[
O_{t+1}=h(S_{t+1}),
\]

and updates:

\[
\hat S_{t+1}=f(\hat S_t,O_{t+1}).
\]

But those observations are no longer fully independent of the original mistake.

This produces the possibility of:

\[
\text{state divergence}
\rightarrow
\text{action}
\rightarrow
\text{environmental change}
\rightarrow
\text{new observation}
\rightarrow
\text{apparent confirmation}.
\]

The divergence can therefore become self-reinforcing.

This connects state-model failure to recursive agentic failure: an initially epistemic error can become embedded in the environment.

## 7. State Fidelity

ASMD proposes **state fidelity** as a first-class agentic safety property.

State fidelity is the degree to which the agent's operative representation correctly preserves the task-relevant:

- facts;
- current state;
- sequence;
- authority relationships;
- provenance;
- uncertainty;
- evidentiary status;
- environmental conditions.

State fidelity is therefore broader than factual recall.

An agent can remember every important sentence and still have low state fidelity if it assigns those sentences the wrong order, meaning, authority, or evidentiary role.

## 8. Predictions

ASMD generates several testable predictions.

**P1.** Agents with strong planning ability but weak state fidelity can produce larger failures than less capable agents.

**P2.** Explicit state verification before planning should reduce failures even when planning ability is unchanged.

**P3.** Explicit representation of authority and supersession should reduce errors involving permissions, revocations, and updated instructions.

**P4.** Provenance tracking should reduce recursive reinforcement by distinguishing independent observations from evidence produced by earlier agent actions.

**P5.** Agents maintaining uncertainty over multiple plausible states should recover from initial errors more readily than agents that prematurely commit to a single state.

**P6.** Many apparently unrelated agentic failures should correlate with measurable divergence between the operative internal state and the externally validated task state.

**P7.** Preserving epistemic class and derivation lineage should reduce evidence-state divergence caused by model-generated inferences re-entering memory as apparent facts.

## 9. Safety Implications

Current agent architectures increasingly externalize memory, state, protocols, and execution control precisely because reconstructing these implicitly from long contexts is unreliable.

ASMD suggests extending this principle.

Before consequential action, an agent should verify:

1. **Task:** What task am I currently performing?
2. **Authority:** Which instruction, constraint, or revision governs?
3. **Evidence:** What supports my present state estimate, where did it come from, and was it observed, retrieved, reported, inferred, or independently verified?
4. **Environment:** What is known, inferred, uncertain, or potentially outdated?

The execution order should become:

\[
\boxed{
\text{construct state}
\rightarrow
\text{verify state}
\rightarrow
\text{plan}
\rightarrow
\text{act}
}
\]

rather than assuming planning can correct an already corrupted state representation.

## 10. Scope

ASMD is not proposed as a theory of every AI failure.

It does not subsume:

- intentional human misuse;
- deliberate model deception;
- conventional cybersecurity compromise;
- reward hacking;
- software defects;
- all forms of goal misalignment.

Its scope is narrower:

> **A large and under-integrated class of non-malicious agentic failures in which a system acts competently on an internally coherent but materially incorrect representation of the task, authority structure, evidence state, or environment.**

The distinctive agentic danger arises when action then changes the environment and makes that incorrect representation harder to detect, correct, or reverse.

## 11. Conclusion

Agentic systems do not act on reality directly. They act on representations of reality.

When:

\[
\hat S_t \neq S_t,
\]

an otherwise aligned and capable system can reason correctly relative to the wrong state and execute the resulting action successfully.

Agency then creates an additional hazard: the action changes the environment from which future state estimates are constructed.

The general failure chain is therefore:

\[
\boxed{
\text{state-model divergence}
\rightarrow
\text{competent action}
\rightarrow
\text{environmental change}
\rightarrow
\text{feedback}
\rightarrow
\text{possible divergence reinforcement}
}
\]

The central safety implication is straightforward:

> **An agent does not need the wrong goal to do the wrong thing. It may only need the wrong state.**

Agentic AI safety should therefore treat **state fidelity** alongside goal alignment, planning reliability, and action control as a fundamental safety property.

## References

- Singh, J., Khan, Z., Prasad, A., Chen, J. C.-Y., Nambi, A., Lee, H., Stengel-Eskin, E., & Bansal, M. (2026). *Agent-BRACE: Decoupling Beliefs from Actions in Long-Horizon Tasks via Verbalized State Uncertainty*.
- Yu, C., Wang, Y., Wang, S., Yang, H., & Ming, L. (2026). *InfiAgent: An Infinite-Horizon Framework for General-Purpose Autonomous Agents*. Findings of ACL 2026.
- Chen, X. (2026). *State-Aware Runtime for Long-Horizon LLM Agents: A Conceptual Framework and Research Agenda*.
- Zhou, C., et al. (2026). *Externalization in LLM Agents: A Unified Review of Memory, Skills, Protocols and Harness Engineering*.

---

*Working paper. The proposed contribution is the ASMD synthesis and its state-fidelity framework, not the prior observation that autonomous agents require reliable state, memory, or belief representations.*