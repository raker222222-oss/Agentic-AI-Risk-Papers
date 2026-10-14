# Open Research Ideas on Agentic AI Risk

### Unmasking Rogues: A Theory of AI Failures

[Read the foundational theory](backward-failure-decomposition/unmasking-rogues-a-theory-of-ai-failures.md) · [Read the integrated monograph](backward-failure-decomposition/MONOGRAPH.md)

*Research programme examining how contemporary rogue AI behavior may be explained through simpler priors in earlier model generations.*

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23040884.svg)](https://doi.org/10.5281/zenodo.23040884)

**Research site:** https://raker222222-oss.github.io/Agentic-AI-Risk-Papers/

**DOI:** [10.5281/zenodo.23040884](https://doi.org/10.5281/zenodo.23040884)

**Independent research ideas and concept notes by Rakesh Rajan (Rakesh OSS) on agentic AI safety, language-mediated state reconstruction, state-model divergence, interpretive failure, sequence integrity, evidentiary reasoning, evidence weighting, relational topology, and visibility bias.**

This repository develops testable ideas about how advanced AI agents can fail in the real world even without malicious intent or independent machine will.

> **Status of this collection:** These are open research ideas, conjectures, pilot observations, and testable problem formulations—not completed empirical papers. The purpose is to make potentially useful failure modes explicit enough for other researchers to test, refine, reject, merge with existing frameworks, or develop experimentally. Giving a concept a name or notation here should not be read as evidence that the phenomenon has already been established. The notes focus on upstream failures in state reconstruction, interpretation, chronology, evidence handling, relational structure, recursive reasoning, state fidelity, and observation boundaries.

## Core tenet: capability growth can change the sophistication of failures

**A central backward investigation hypothesis is that an improving model may retain, suppress, compensate for, or transform an earlier weakness while acquiring the ability to express that weakness in more sophisticated or consequential ways.** Better overall benchmarks do not imply that all underlying control problems have been reduced to zero. Nor does a later, more elaborate failure require an identical earlier incident: backward analysis seeks simpler manifestations of the relevant failure family.

**Direct published illustration from Google:** The *Gemini 1.5 Technical Report* notes that improved text understanding and instruction following may help explain susceptibility to certain human-readable adversarial instructions, even as other jailbreak resistance improved. The *Gemini 2.5 Technical Report* reports that greater Gemini 2.0 capability enabled some more effective natural-language attacks despite gains against other methods; subsequent adversarial training improved Gemini 2.5 defenses, while the more capable 2.5 Pro remained less resilient than 2.5 Flash on the reported tests. These observations concern *attack susceptibility*, not direct proof of the shutdown failure's internal origins. They furnish a longitudinal illustration of capability-dependent changes in failure expression and defense effectiveness. Sources: [Gemini 1.5 Technical Report](https://arxiv.org/abs/2403.05530); [Gemini 2.5 Technical Report](https://storage.googleapis.com/deepmind-media/gemini/gemini_v2_5_report.pdf).

**Mandatory case-analysis question:** Starting with the latest documented failure, what simpler constraint, authority, goal, or evidence-handling imperfection can reasonably be inferred backward in named predecessor models? What new capability or scaffold could have changed the later manifestation? What published evidence favors elimination, suppression, transformation, or compensation? Record counterexamples and improvements, and distinguish observation from inference. Do not reverse the argument by starting with an old defect and attributing modern incidents to it.


## Case-selection requirements

backward investigation begins with a documented incident in a **specifically identifiable model** and works backward through that model's technical, training, and research lineage to isolate earlier components of the failure.

**Incident model identification is a primary eligibility requirement.** A case must identify the responsible model by name and version, and preferably by checkpoint or release identifier, using verifiable incident reports, technical papers, evaluation records, appendices, or independent research. A product name, agent name, or provider name alone does not identify the incident model; cases without a sufficiently specific model identifier are deferred or excluded.

Priority goes to cases with accessible primary incident evidence and documented technical or training predecessors. Model lineage must be distinguished from product-release chronology: a newer model name does not, by itself, establish inherited weights, training data, mechanisms, or behavior. External historical analogues are investigated separately and must not be presented as demonstrated ancestors of the incident model. Where direct causal inheritance is unknown, the analysis explicitly identifies the evidence gap.

## Theory: persistence, suppression, transformation and compensation

backward investigation is a broad, retrospective **theory under examination across multiple documented cases**, not a claim to have established internal causation in any particular incident. Each study begins with an **identified incident model** (version and, when available, checkpoint), a primary incident record, and a documented developmental or research lineage. Cases that identify only a product, agent or provider are deferred. Earlier manifestations need not reproduce the endpoint incident: the theory asks whether **simpler limitations in the same failure family** can be observed in earlier generations and whether added training, reasoning, constraints, tool access and scaffolding could alter their expression or consequences.

backward investigation distinguishes four possibilities:

- **Elimination:** a weakness has genuinely ceased to operate.
- **Suppression:** its measured manifestations decline under tested conditions, but it may still occur elsewhere.
- **Transformation:** a related weakness changes form or consequences as capabilities and environments change.
- **Compensation:** another model component, external control or scaffold prevents a remaining weakness from producing an observable failure.

These are competing possibilities, **not assumptions that all earlier flaws persist**. Successive training, fine-tuning, alignment, reinforcement learning, instruction hierarchies and scaffolding may improve measured reliability without proving a primitive issue has been nullified to zero. Zero failures in finite testing mean zero **observed** failures in those conditions, not demonstrated universal elimination. The relevant question is whether interventions eliminate, suppress, transform or compensate for the weakness; public observations often cannot distinguish them.

The case studies test the **explanatory reach and limits of this theory collectively**. Public reports, model cards, appendices and independent evaluations can support or challenge a proposed developmental pattern; behavioral resemblance alone cannot prove training inheritance or internal causation. Technical validation may require inaccessible checkpoints, training records, interventions and representation studies. A backward inquiry could ultimately extend beyond model versions into learning or language acquisition, but that remains an open hypothesis, not an established endpoint.

## Master framework

The series is organized around an upstream architectural problem: **language is a compressed representation of state, while a language model often has to reconstruct state from that compressed representation.** Because the inverse is underdetermined, learned priors participate directly in state construction.

The proposed failure chain is:

**lossy linguistic representation → underdetermined state reconstruction → prior-driven selection → coherence preservation → epistemic relation distortion → wrong operative state → competent action → feedback and possible reinforcement.**

This master framework is developed in [Language-Mediated State Reconstruction in Agentic AI](06-language-mediated-state-reconstruction.md).

## Research themes

- **Language-mediated state reconstruction** — why recovering world or task state from compressed linguistic evidence is an underdetermined inverse problem, and how learned priors can become structural substitutes for missing state.
- **Coherence-Dominant Epistemic Reconstruction (CDER)** — how a dominant reconstructed state can preserve narrative coherence by reweighting evidence, downgrading anomalies, or hardening inferences without new evidence.
- **Agentic state-model divergence and state fidelity** — how aligned and competent agents can act dangerously when their operative representation of the task, authority structure, evidence state, or environment diverges from governing reality.
- **Agentic AI safety and autonomous agents** — failure modes that appear when AI systems plan, retrieve information, use tools, and act over time.
- **Interpretive failure in large language models** — how an early misunderstanding can reshape later reasoning and action.
- **Sequence integrity and long-context memory** — why correct facts in the wrong order can produce an incorrect world state and unsafe action.
- **Relational topology loss** — how conversational elements can remain present and retrievable while already-present functional relations among them are misused, producing an incorrect reconstruction of human meaning, intention, or relationship state.
- **Recursive amplification** — how an initial interpretive error can alter the environment and generate apparent confirmation of the original mistake.
- **Evidentiary threshold distortion** — how demanding explicit proof when convergent evidence is operationally sufficient can cause dangerous underreaction.
- **Narrative evidence weight distortion** — how a model can retain the right evidence yet misinterpret a narrative by assigning the wrong relative importance to explicit statements, behavioural patterns, baseline changes, source asymmetries, and culturally conditioned signals.
- **Visible-system agency distortion** — how AI can mistake prominence within a partial information channel for overall real-world agency when consequential activity is distributed unevenly across visible and hidden channels.
- **Corpus-shaped human-state interpretation** — how overlapping language for different human states can interact with corpus asymmetry and produce premature collapse toward a dominant latent-state reconstruction.

## Research ideas
1. [How AI Distorts Meaning!](01-ai-mediated-interpretive-displacement.md) — **AI-Mediated Interpretive Displacement (AMID):** how AI interpretation can become a hidden causal participant in human communication.
2. [AI Amplifies Its Own Mistakes to Truth](02-recursive-amplification-agentic-ai.md) — **Recursive Amplification of Interpretive Failure (RAIF):** how an initial interpretive error can alter later evidence and recursively strengthen itself.
3. [Right Facts, Wrong Order, Wrong Action](03-sequence-integrity-agentic-ai.md) — **Sequence Integrity:** why chronology, precedence, procedural order, and revision history matter for agentic action.
4. [Proof? Just Ask AI to Define It!](04-evidentiary-threshold-distortion.md) — **Evidentiary Threshold Distortion (ETD):** how an excessive proof threshold can cause underreaction despite convergent evidence.
5. [The Agent Has the Right Goal and the Wrong World](05-agentic-state-model-divergence.md) — **Agentic State-Model Divergence (ASMD):** how an aligned agent can act competently on the wrong representation of reality.
6. [AI Reconstructs Reality From Language—and Can Reconstruct It Wrong](06-language-mediated-state-reconstruction.md) — **Language-Mediated State Reconstruction:** the master framework connecting underdetermined language-to-state reconstruction to prior-driven state construction and agentic failure.
7. [Narrative Evidence Weight Distortion in Large Language Models](07-narrative-evidence-weight-distortion.md) — **Narrative Evidence Weight Distortion (NEWD):** how correct evidence can still yield a wrong interpretation when relative evidentiary weights are distorted.
8. [Visibility Within an Information System Is Not Agency in the Real World](08-visible-system-agency-distortion.md) — **Channel-to-Total Generalization Error (CTGE):** how visibility within a partial channel can be mistaken for overall real-world agency; includes exploratory pilot evidence.
9. [The Annotation Tax: Relational Topology Loss in Human–LLM Conversation](09-annotation-tax-relational-topology-loss.md) — **Relational Topology Loss (RTL):** how models can retain conversational elements while failing to correctly operationalize already-present relations that determine meaning; distinguishes information availability from relational operationalization and introduces the Excess Annotation Tax.
10. [Human State and Corpus-Shaped Interpretation](10-human-state-corpus-shaped-interpretation.md) — a theory of how human-state underdetermination, corpus asymmetry and interpretive collapse can make an LLM statistically faithful to language while wrong about the human state that produced it.

## Core proposition

The most upstream formulation is:

**language is a lossy projection of state; reconstructing state from language is underdetermined; probable reconstruction is not necessarily epistemically warranted reconstruction.**

The master failure chain is:

**lossy linguistic representation → underdetermined state reconstruction → prior-driven selection → coherence preservation → epistemic relation distortion → wrong operative state → competent action → environmental feedback.**

The broader ASMD formulation is:

**state-model divergence → competent action → environmental change → feedback → possible divergence reinforcement.**

An upstream EID formulation is:

**insufficient information → prior substitution → premature commitment → wrong state model → wrong action.**

The relational epistemic formulation is:

**retained information + unstable epistemic relations → reconstructed operative state → state-model divergence → action.**

Or, in its simplest form:

**memory fidelity ≠ epistemic fidelity.**

Human misuse creates a separate risk:

**human intent + frontier AI capability + tools + automation + access → disproportionate operational power.**

## Keywords

Agentic AI, AI agents, autonomous agents, AI safety, frontier AI, artificial intelligence safety, LLM safety, large language models, language-mediated state reconstruction, linguistic inverse problem, probabilistic world-state recovery, prior-dominant state construction, Coherence-Dominant Epistemic Reconstruction, CDER, relational topology loss, provenance, inference status, authority hierarchy, agentic state-model divergence, state fidelity, uncertainty, belief state, agent memory, long-context memory, sequence integrity, temporal reasoning, interpretive failure, recursive reasoning, recursive amplification, evidentiary reasoning, narrative evidence weight distortion, NEWD, training-induced narrative weight priors, TINWP, visible-system agency distortion, channel-to-total generalization error, CTGE, actor-correlated modality missingness, ACMM, cultural evidence weighting, AI hallucination, tool-using agents, agentic misalignment, machine agency, AI governance.

## Citation

Rajan, Rakesh. *Agentic AI Risk Papers*. Version 1.0.0. Zenodo. https://doi.org/10.5281/zenodo.23040884

## Status

These are independent research ideas and concept notes intended to state falsifiable propositions, conceptual models, experimental designs, and position arguments. They are not peer reviewed.

## Author

**Rakesh Rajan — Rakesh OSS**

Independent research ideas and concept notes on agentic AI risk, language-mediated state reconstruction, interpretation, sequencing, evidence weighting, state fidelity, relational topology, and partial-observation bias.