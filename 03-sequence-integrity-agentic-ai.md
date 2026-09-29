# Sequence Integrity as an Agentic AI Safety Problem

**Working paper**

## Abstract

Many tasks are not defined only by what facts are present, but by the order in which those facts occurred. Large language models can sometimes preserve individual details while weakening, compressing, or rearranging chronology. In ordinary conversation this may produce a mistaken interpretation. In agentic systems, sequence errors can become operational errors.

This paper proposes **Sequence Integrity** as a distinct agentic-AI safety requirement: a system must preserve the relevant temporal and procedural ordering of observations, instructions, permissions, state changes, and actions. The core claim is that correct elements in the wrong order can produce an incorrect state model and therefore an incorrect action.

## 1. Order Is Part of Meaning

Consider events:

\[
E = \{e_1,e_2,e_3,e_4\}.
\]

A bag-of-facts representation preserves membership but not sequence.

Yet:

\[
(e_1 \rightarrow e_2 \rightarrow e_3 \rightarrow e_4)
\neq
(e_3 \rightarrow e_1 \rightarrow e_4 \rightarrow e_2).
\]

The same facts may imply different causes, permissions, obligations, or interpretations depending on their order.

## 2. Sequence Compression

LLMs often summarize long interactions. Compression can preserve salient content while losing timing relationships such as:

- before versus after;
- request versus response;
- cause versus consequence;
- permission granted versus permission revoked;
- old state versus current state;
- first attempt versus later correction.

This creates **sequence compression error**.

## 3. Chronology and Human Inference

Humans commonly infer meaning from patterns across time.

For example:

1. an instruction is issued;
2. it is later modified;
3. the original instruction is then quoted again.

A system that remembers both instructions but not the modification order may execute the obsolete instruction.

Similarly, in interpersonal interpretation, a message sent before a conflict cannot rationally be treated as a reaction to that later conflict.

## 4. Agentic Sequence Failure

In agentic systems, sequence errors may affect execution directly.

Let state transition be:

\[
S_{t+1}=T(S_t,A_t).
\]

If the agent reconstructs an incorrect prior state \(\hat{S}_t\), then even a locally reasonable action policy \(\pi\) may produce the wrong action:

\[
A_t=\pi(\hat{S}_t).
\]

Thus the error can arise before planning begins.

## 5. Instruction Precedence

Sequence integrity includes precedence.

Suppose:

- at \(t_1\): permission granted;
- at \(t_2\): permission narrowed;
- at \(t_3\): permission revoked.

A system must not aggregate these into “permission was granted at some point.”

The current operational state depends on the latest valid transition.

## 6. Mis-Sequenced Evidence

Evidence also changes meaning with timing.

An anomaly observed before an intervention is different from the same anomaly observed after the intervention.

If the system misorders them, it may mistake consequence for cause.

This links sequence integrity to recursive interpretive amplification: a chronology failure can make self-generated evidence appear independent.

## 7. Long-Context Vulnerability

As context grows, systems may retain many details while weakening exact temporal relations.

This creates a dangerous illusion of completeness: the model appears to remember everything important, but the ordering needed to interpret those facts correctly has degraded.

A high-recall but low-sequence-integrity system can therefore be more dangerous than one that openly forgets details.

## 8. Procedural Sequence

Sequence integrity is not only chronological. Many workflows require ordered procedural constraints:

\[
A \rightarrow B \rightarrow C
\]

where executing \(C\) before \(B\) is unsafe even if all three steps are individually correct.

Examples include:

- authenticate, then authorize, then execute;
- verify, then approve, then transfer;
- obtain consent, then collect data;
- validate dependencies, then deploy.

## 9. Sequence Integrity Definition

Define **Sequence Integrity (SI)** as the degree to which a system preserves and acts on all task-relevant ordering relations among events, instructions, observations, and state transitions.

If \(R\) is the set of true ordering relations and \(\hat{R}\) the system's reconstructed relations, then a simple measure is:

\[
SI = \frac{|R \cap \hat{R}|}{|R|}.
\]

This can be extended by weighting safety-critical relations more heavily.

## 10. Main Hypotheses

**H1.** Sequence accuracy will degrade faster than fact recall as interaction length increases.

**H2.** Systems will sometimes generate correct local reasoning from an incorrectly reconstructed chronology.

**H3.** Agentic tasks with state-changing actions will produce larger consequences from sequence errors than answer-only tasks.

**H4.** Explicit timestamping and event-ledger representations will reduce sequence failures.

**H5.** Asking models to reconstruct chronology before interpretation or action will improve downstream accuracy.

**H6.** Sequence errors will be especially consequential where permissions, revocations, dependencies, or causal attribution are involved.

## 11. Experimental Design

Construct tasks with identical facts but different event orders.

Test models on:

- chronology reconstruction;
- causal attribution;
- current-permission state;
- next-action selection;
- procedural execution.

Vary:

- context length;
- number of temporal reversals;
- presence or absence of timestamps;
- narrative versus structured event-log format;
- single-turn versus multi-step agentic execution.

Measure both fact recall and ordering accuracy separately.

## 12. Critical Control

A model may fail because it forgot facts rather than because it mis-sequenced them.

Experiments should therefore include cases where all events are correctly recalled but the relative order is tested independently.

The theory concerns:

\[
\text{facts retained} + \text{order corrupted}.
\]

## 13. Falsification

The theory would be weakened if:

- ordering accuracy remains comparable to fact recall across long contexts;
- agents rarely act incorrectly when chronology alone is manipulated;
- timestamps and event ledgers provide little improvement;
- procedural reordering does not materially affect execution accuracy;
- models reliably distinguish cause from consequence even under sequence stress.

## 14. Design Implications

Agentic systems should maintain explicit representations of:

- timestamped events;
- state transitions;
- instruction supersession;
- permission changes;
- causal provenance;
- completed and pending procedural steps.

Before consequential action, the system should verify the relevant sequence rather than reconstructing it implicitly from prose memory.

## 15. Conclusion

Agentic safety depends not only on remembering the right facts but on remembering what came before what.

The failure chain is:

\[
\boxed{
\text{correct facts}
\rightarrow
\text{wrong order}
\rightarrow
\text{wrong state model}
\rightarrow
\text{wrong action}
}
\]

Sequence integrity should therefore be treated as a first-class safety property rather than as a minor aspect of memory quality.

---

*This is a working paper intended to state testable propositions. It is not peer reviewed.*
