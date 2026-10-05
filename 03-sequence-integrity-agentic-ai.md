# Right Facts, Wrong Order, Wrong Action
## Sequence Integrity as an Agentic AI Safety Problem


**Status: Open research idea / concept note.**

> This note presents a proposed failure mode, mechanism, or research question for further investigation. It is **not presented as a completed empirical paper or as an experimentally established theory**. Where prior research or pilot observations are discussed, they motivate the idea; the broader claims remain hypotheses to be tested, refined, or falsified.

## Research idea summary
Many tasks are not defined only by what facts are present, but by the order in which those facts occurred. Large language models can sometimes preserve individual details while weakening, compressing, or rearranging chronology. In ordinary conversation this may produce a mistaken interpretation. In agentic systems, sequence errors can become operational errors.

Adjacent research already demonstrates important parts of this problem. **Lost in the Middle** shows that long-context performance depends strongly on where relevant information appears, long-horizon memory benchmarks such as **LongMemEval** test temporal reasoning and updating over extended interactions, and **Control Illusion** shows that models can fail to preserve explicit instruction hierarchy under competing priors. Sequence Integrity does not claim that position effects, temporal reasoning failures, or instruction-priority failures are new.

This research idea proposes the narrower safety requirement **Sequence Integrity**: an agent must preserve the task-relevant temporal, procedural, supersession, and discourse-authority relations among observations, instructions, permissions, state changes, and actions. The core claim is that correct elements in the wrong order—or retained statements with the wrong governing authority—can produce an incorrect state model and therefore an incorrect action.

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

## 9. Discourse Authority and Prior-Dominant Override

Sequence integrity also includes **hierarchical dependency**. Instructions, clarifications, questions, answers, permissions, exceptions, and revisions do not merely appear in an order; some elements define how later elements are to be interpreted.

For example:

\[
\text{instruction}
\rightarrow
\text{clarification}
\rightarrow
\text{response}
\]

The response is not semantically autonomous. Its role is constrained by the instruction and clarification that precede it.

A significant safety failure occurs when an LLM retains every relevant token but allows a learned semantic prior activated by later content to acquire greater interpretive weight than the explicit hierarchy that should govern that content. The agent may then preserve the text while reversing its authority structure.

Let \(H\) denote the explicit discourse hierarchy and \(P\) a learned semantic prior activated by the content. A safe interpretation should approximate:

\[
I = f(P \mid H),
\]

so that the prior is evaluated inside the governing structure.

A **prior-dominant override** occurs when:

\[
I = f(H \mid P),
\]

so that the hierarchy itself is reinterpreted through the activated prior.

The failure chain is:

\[
\text{explicit hierarchy}
\rightarrow
\text{semantic prior activation}
\rightarrow
\text{hierarchy underweighted}
\rightarrow
\text{wrong state model}
\rightarrow
\text{wrong action}.
\]

This is not ordinary forgetting. The system may correctly reproduce the instruction, question, clarification, or constraint while failing to grant it the authority required to control later interpretation.

For agentic systems, this is hazardous because instructions, prohibitions, exceptions, and approvals are often hierarchical rather than merely sequential. A system that treats those relations as soft probabilistic cues can appear to understand the entire interaction while acting against its operative meaning.

## 10. Sequence Integrity Definition

Define **Sequence Integrity (SI)** as the degree to which a system preserves and acts on all task-relevant ordering and dependency relations among events, instructions, observations, and state transitions.

If \(R\) is the set of true ordering or authority relations and \(\hat{R}\) the system's reconstructed relations, then a simple measure is:

\[
SI = \frac{|R \cap \hat{R}|}{|R|}.
\]

This can be extended by weighting safety-critical relations more heavily.

## 11. Main Hypotheses

**H1.** Sequence accuracy will degrade faster than fact recall as interaction length increases.

**H2.** Systems will sometimes generate correct local reasoning from an incorrectly reconstructed chronology.

**H3.** Agentic tasks with state-changing actions will produce larger consequences from sequence errors than answer-only tasks.

**H4.** Explicit timestamping and event-ledger representations will reduce sequence failures.

**H5.** Asking models to reconstruct chronology before interpretation or action will improve downstream accuracy.

**H6.** Sequence errors will be especially consequential where permissions, revocations, dependencies, or causal attribution are involved.

**H7.** Models will sometimes preserve the literal content of a governing instruction or clarification while allowing semantically salient subordinate content to override its operational authority.

**H8.** Explicit representation of discourse roles and authority relations will reduce prior-dominant overrides.

## 12. Experimental Design

Construct tasks with identical facts but different event orders and authority structures.

Test models on:

- chronology reconstruction;
- causal attribution;
- current-permission state;
- next-action selection;
- procedural execution;
- instruction versus clarification precedence;
- governing versus subordinate discourse roles.

Vary:

- context length;
- number of temporal reversals;
- presence or absence of timestamps;
- narrative versus structured event-log format;
- single-turn versus multi-step agentic execution;
- strength of semantically salient but subordinate content.

Measure fact recall, ordering accuracy, and authority-relation accuracy separately.

## 13. Critical Control

A model may fail because it forgot facts rather than because it mis-sequenced or misweighted them.

Experiments should therefore include cases where all events and instructions are correctly recalled but their relative order or authority is tested independently.

The theory concerns:

\[
\text{facts retained} + \text{sequence or authority corrupted}.
\]

## 14. Falsification

The theory would be weakened if:

- ordering accuracy remains comparable to fact recall across long contexts;
- agents rarely act incorrectly when chronology alone is manipulated;
- timestamps and event ledgers provide little improvement;
- procedural reordering does not materially affect execution accuracy;
- models reliably distinguish cause from consequence even under sequence stress;
- models reliably preserve governing discourse authority despite strong competing semantic priors.

## 15. Design Implications

Agentic systems should maintain explicit representations of:

- timestamped events;
- state transitions;
- instruction supersession;
- permission changes;
- causal provenance;
- completed and pending procedural steps;
- discourse roles;
- governing versus subordinate instructions and responses.

Before consequential action, the system should verify not only the relevant sequence but also the authority relations that determine how later content is to be interpreted.

## 16. Conclusion

Agentic safety depends not only on remembering the right facts but on preserving what came before what and which elements govern the meaning of others.

The failure chain is:

\[
\boxed{
\text{correct content}
\rightarrow
\text{sequence or authority relation corrupted}
\rightarrow
\text{wrong state model}
\rightarrow
\text{wrong action}
}
\]

A particularly dangerous case occurs when learned semantic priors override explicit instruction or discourse hierarchy. The system may retain every relevant token and still invert the operative meaning of the interaction.

Sequence integrity should therefore be treated as a first-class safety property rather than as a minor aspect of memory quality.

---

*This is a working paper intended to state testable propositions. It is not peer reviewed.*

## Research status and next steps

This idea is offered for further thought and empirical development. Its value depends on whether controlled tests can distinguish the proposed failure from adjacent explanations, reproduce it across models and tasks, and identify conditions under which it weakens or disappears. Negative results, narrower boundary conditions, or evidence that an existing framework already explains the effect would all be informative.
