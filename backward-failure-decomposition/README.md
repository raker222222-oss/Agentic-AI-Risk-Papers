# The Ghosts in the Machine

**Reverse Failure Analysis (RFA) is a method for tracing a documented AI failure backward through its model-development lineage, progressively decomposing it until the smallest identifiable problem capable of contributing to the final incident is found.**

**Tracing AI Failures Backward** — Reverse Failure Analysis (RFA), integrated research monograph, v1.1 (10 October 2026), R. Rajan.

**[Read the complete monograph](MONOGRAPH.md)**

The work comprises one foundational theory, six case-specific backward investigations, comparative synthesis of the original four cases, and a research programme. Cross-case convergence analysis is deferred. These are exploratory applications, not conclusive demonstrations of universal ancestral failures.

## RFA tenet: capability growth can change the sophistication of failures

**A central RFA hypothesis is that an improving model may retain, suppress, compensate for, or transform an earlier weakness while acquiring the ability to express that weakness in more sophisticated or consequential ways.** Better overall benchmarks do not imply that all underlying control problems have been reduced to zero. Nor does a later, more elaborate failure require an identical earlier incident: backward analysis seeks simpler manifestations of the relevant failure family.

**Direct published illustration from Google:** The *Gemini 1.5 Technical Report* notes that improved text understanding and instruction following may help explain susceptibility to certain human-readable adversarial instructions, even as other jailbreak resistance improved. The *Gemini 2.5 Technical Report* reports that greater Gemini 2.0 capability enabled some more effective natural-language attacks despite gains against other methods; subsequent adversarial training improved Gemini 2.5 defenses, while the more capable 2.5 Pro remained less resilient than 2.5 Flash on the reported tests. These observations concern *attack susceptibility*, not direct proof of the shutdown failure's internal origins. They furnish a longitudinal illustration of capability-dependent changes in failure expression and defense effectiveness. Sources: [Gemini 1.5 Technical Report](https://arxiv.org/abs/2403.05530); [Gemini 2.5 Technical Report](https://storage.googleapis.com/deepmind-media/gemini/gemini_v2_5_report.pdf).

**Mandatory case-analysis question:** Starting with the latest documented failure, what simpler constraint, authority, goal, or evidence-handling imperfection can reasonably be inferred backward in named predecessor models? What new capability or scaffold could have changed the later manifestation? What published evidence favors elimination, suppression, transformation, or compensation? Record counterexamples and improvements, and distinguish observation from inference. Do not reverse the argument by starting with an old defect and attributing modern incidents to it.


## Reading order

- [01-the-fault-beneath-the-fix.md](./01-the-fault-beneath-the-fix.md)
- [02-from-hugging-face-back-to-neural-networks.md](./02-from-hugging-face-back-to-neural-networks.md)
- [03-when-the-score-becomes-the-goal.md](./03-when-the-score-becomes-the-goal.md)
- [04-the-agent-that-changed-the-assignment.md](./04-the-agent-that-changed-the-assignment.md)
- [05-the-grader-became-the-target.md](./05-the-grader-became-the-target.md)
- [08-the-threat-behind-the-task.md](./08-the-threat-behind-the-task.md) — Case 05
- [09-the-agent-that-would-not-stop.md](./09-the-agent-that-would-not-stop.md) — Case 06
- [06-comparative-findings.md](./06-comparative-findings.md)
- [07-the-hunt-for-ais-hidden-faults.md](./07-the-hunt-for-ais-hidden-faults.md)

## RFA theory: persistence, suppression, transformation and compensation

RFA is a broad, retrospective **theory under examination across multiple documented cases**, not a claim to have established internal causation in any particular incident. Each study begins with an **identified incident model** (version and, when available, checkpoint), a primary incident record, and a documented developmental or research lineage. Cases that identify only a product, agent or provider are deferred. Earlier manifestations need not reproduce the endpoint incident: the theory asks whether **simpler limitations in the same failure family** can be observed in earlier generations and whether added training, reasoning, constraints, tool access and scaffolding could alter their expression or consequences.

RFA distinguishes four possibilities:

- **Elimination:** a weakness has genuinely ceased to operate.
- **Suppression:** its measured manifestations decline under tested conditions, but it may still occur elsewhere.
- **Transformation:** a related weakness changes form or consequences as capabilities and environments change.
- **Compensation:** another model component, external control or scaffold prevents a remaining weakness from producing an observable failure.

These are competing possibilities, **not assumptions that all earlier flaws persist**. Successive training, fine-tuning, alignment, reinforcement learning, instruction hierarchies and scaffolding may improve measured reliability without proving a primitive issue has been nullified to zero. Zero failures in finite testing mean zero **observed** failures in those conditions, not demonstrated universal elimination. The relevant question is whether interventions eliminate, suppress, transform or compensate for the weakness; public observations often cannot distinguish them.

The case studies test the **explanatory reach and limits of this theory collectively**. Public reports, model cards, appendices and independent evaluations can support or challenge a proposed developmental pattern; behavioral resemblance alone cannot prove training inheritance or internal causation. Technical validation may require inaccessible checkpoints, training records, interventions and representation studies. A backward inquiry could ultimately extend beyond model versions into learning or language acquisition, but that remains an open hypothesis, not an established endpoint.

## Evidence boundary

**Primary track:** backward reconstruction in the target model-development family, including dated model-stage observations, safeguards, and supported research/method transmission bridges. **Secondary track:** unrelated historical analogues, kept separate and never treated as proof of ancestry. Open questions and missing links are retained.

Status: public research preprint; not peer-reviewed. The existing repository's earlier papers are independent from this monograph.

## Two-line case research

Each case distinguishes **Line 1 (model-family developmental history)** from **Line 2 (the independently traced scientific history of the smaller problem)**. Cases 01–05 were updated with Line 2 sections; Case 06 includes both lines, beginning Line 2 in 2026. The [integrated monograph](MONOGRAPH.md) includes these supplements. Historical parallels never count as model checkpoints by resemblance alone.

## Case 07 (investigation underway)

- [Case 07: Claude Haiku 4.5 external research admission ledger](./10-the-agent-that-filed-a-false-tip-research-ledger.md) — Claude-tested studies in Line 1; other historical problem studies in Line 2. This is a research ledger, not a completed case.

## Case 08 — Published research investigation

- [The Simulation That Escaped: When the Task Outran Its Authority](./11-the-simulation-that-escaped.md) — Mythos 5 real-internet cybersecurity evaluation, four-part RFA decomposition, Anthropic company research (Line 1), independent historical foundations (Line 2), and repair-depth evaluation. Retrospective published research only; no original model experiments.

---

## Founder-mediated Line 1 research extension — 10 October 2026

**Revised Line 1 admission rule (10 October 2026).** Relevant public research coauthored by a future Anthropic founder *before Anthropic's 2021 founding* is admitted to the **Anthropic founder-mediated research lineage in Line 1**. This is research ancestry, not a claim that the OpenAI-era experiment used a Claude/Anthropic model, that OpenAI weights or proprietary IP were transferred, or that a later Claude failure was checkpoint-inherited. Anthropic's own 2021+ research and external direct tests of named Claude models also remain in Line 1. Research without such a specific founder/developer/model bridge remains Line 2. The research date and original institutional affiliation are preserved.

**Research-boundary correction:** In Anthropic cases, Line 1 includes documented relevant work by eventual Anthropic founders before 2021, even when the work occurred at OpenAI. This is a *founder-mediated scientific lineage*, distinct from Anthropic's independently trained Claude model ancestry. Verified published research now reaches 2016 (Amodei/Olah et al.), with 2017 preference learning, 2018 debate, 2019 language preference/reward evaluation and 2020 few-shot language-model studies. Individual case strength varies; case 09 is still unpublished.

**Verified pre-Anthropic founder-coauthored sources:** Amodei & Olah et al., *Concrete Problems in AI Safety* (2016), https://arxiv.org/abs/1606.06565 ; Christiano, Leike, Brown et al. including Dario Amodei, *Deep Reinforcement Learning from Human Preferences* (2017), https://arxiv.org/abs/1706.03741 ; Irving, Christiano & Amodei, *AI Safety via Debate* (2018), https://arxiv.org/abs/1805.00899 ; Ziegler, Stiennon, Wu et al. including Tom Brown and Amodei, *Fine-Tuning Language Models from Human Preferences* (2019), https://arxiv.org/abs/1909.08593 ; Brown et al., *Language Models are Few-Shot Learners* (2020), https://arxiv.org/abs/2005.14165 .
