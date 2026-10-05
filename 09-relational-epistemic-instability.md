# Relational Epistemic Instability in Agentic AI
## Why Remembering the Facts Is Not Enough

**Rakesh Rajan (Rakesh OSS)**  
**Status: Open research idea / concept note.**

> This note presents a proposed failure mode, mechanism, or research question for further investigation. It is **not presented as a completed empirical paper or as an experimentally established theory**. Where prior research or pilot observations are discussed, they motivate the idea; the broader claims remain hypotheses to be tested, refined, or falsified.

Position paper

## Research idea summary
Agentic AI research has increasingly improved memory, retrieval, provenance, uncertainty estimation, belief-state maintenance, and instruction following. Adjacent work already provides important pieces of this problem: **Structured Episodic Event Memory** and **Hindsight** preserve structured memory and provenance; **Belief Memory** and **Agent-BRACE** preserve uncertainty under partial observability; **Control Illusion** documents instruction-hierarchy failures; and self-auditing and relational-uncertainty methods address unsupported belief propagation and dependency structure. REI does not claim that any of these individual problems are new.

This research idea proposes the narrower higher-order failure class **Relational Epistemic Instability (REI)**: an AI system may retain substantially the same information while changing the epistemic relationships among that information as framing, salience, or context changes. It further proposes **Coherence-Dominant Epistemic Reconstruction (CDER)** as a possible generative mechanism: when semantic coherence conflicts with preserved epistemic structure, the system may maintain a coherent interpretation by reconstructing the roles of retained information. Evidence can be reweighted, anomalies downgraded, inferences promoted into premises, or authority and sequence weakened without corresponding new evidence. A temporal pathway, **epistemic laundering**, can then cause model-generated inferences to re-enter memory as apparent facts. The proposed safety principle is that some properties of information should behave as **epistemic invariants**.

---

## 1. The Epistemic Blind Spot

A large language model agent does not merely need access to information. It must preserve what that information **means epistemically**.

Current systems increasingly provide agents with larger context windows, external memory, vector retrieval, episodic memory, knowledge graphs, explicit belief states, provenance tracking, and uncertainty mechanisms. These are important advances. But flat content retention is not enough.

The central distinction is:

\[
\text{content fidelity} \neq \text{epistemic fidelity}.
\]

Or more concretely:

\[
\text{node preservation} \not\Rightarrow \text{relation preservation}.
\]

An agent may remember every node in an evidence set while reconstructing the edges differently.

---

## 2. Operative Epistemic Structure

Let the agent retain:

\[
E=\{e_1,e_2,\ldots,e_n\}.
\]

Each item also has an epistemic role:

\[
R(e_i)=\{
\text{source},
\text{time},
\text{authority},
\text{status},
\text{uncertainty},
\text{dependency},
\text{evidentiary role}
\}.
\]

The operative epistemic structure is therefore:

\[
\mathcal{R}(E).
\]

A system may preserve:

\[
E_{t+1}=E_t
\]

while allowing:

\[
\mathcal{R}_{t+1}(E) \neq \mathcal{R}_t(E).
\]

No fact was deleted. Yet the state from which the agent reasons has changed.

This is **Relational Epistemic Instability**.

---

## 3. Epistemic Invariants

Some relations should change when new evidence arrives. They should not change merely because a different interpretation becomes more coherent.

We call these protected properties **epistemic invariants**.

### Observation / inference status

A model-generated inference should not silently become an observed fact through repetition.

### Provenance

The origin and derivation history of a proposition should remain attached to it.

### Temporal order

If event \(A\) occurred before event \(B\), reinterpretation may change what that sequence means but should not change the sequence itself.

### Authority

If instruction \(I_2\) supersedes \(I_1\), semantic salience should not restore \(I_1\) to operative authority.

### Uncertainty

An unresolved proposition should not become certain merely because it fits a coherent narrative.

### Contradiction and anomaly status

A contradictory observation should remain represented as a contradiction until it is explained rather than being silently demoted to noise.

---

## 4. Why This Is Not Just Memory Failure

Memory failure asks:

> Was the information retained?

Relational epistemic failure asks:

> Was the role of the information retained?

Thus:

\[
\text{perfect recall}
\not\Rightarrow
\text{stable epistemic state}.
\]

A model can remember the relevant sentences while reweighting, reordering, reclassifying, or detaching them from provenance.

---

## 5. Coherence-Dominant Epistemic Reconstruction

Framing effects are well established. REI makes a stronger claim: framing may change not merely the answer, but the epistemic organization of unchanged evidence.

We propose **Coherence-Dominant Epistemic Reconstruction (CDER)** as one possible mechanism behind this instability.

Let \(F\) be the currently dominant semantic frame. A structurally faithful reasoner should preserve the relevant epistemic relationships in \(\mathcal{R}(E)\) and evaluate candidate interpretations against them.

Under CDER, the process may instead behave approximately as:

\[
F
\rightarrow
\mathcal{R}_F(E)
\rightarrow
N,
\]

where \(N\) is a coherent narrative and \(\mathcal{R}_F(E)\) is a frame-conditioned reconstruction of the relationships among otherwise retained information.

The central hypothesis is:

> **When semantic coherence and preserved epistemic structure conflict, an LLM may preferentially preserve coherence by reconstructing the epistemic relations among retained information.**

This can manifest as:

- evidence compatible with the dominant frame receiving greater weight;
- contradictory observations remaining visible but losing constraining force;
- tentative inferences becoming operative premises;
- background constraints losing authority;
- person, event, source, or temporal bindings shifting toward the coherent interpretation;
- uncertainty shrinking without new discriminating evidence.

The important distinction is that the underlying information can remain substantially unchanged:

\[
E \text{ fixed},\qquad F_1\neq F_2,
\]

while:

\[
\mathcal{R}(E\mid F_1)\neq\mathcal{R}(E\mid F_2).
\]

This explains why the same model can sometimes produce two different, internally coherent narratives from essentially the same evidence after a framing change or correction.

CDER should be treated as a behavioral hypothesis, not as a claim about a demonstrated latent-space or attention mechanism.

---

## 6. A Unifying Pattern Across Apparently Separate Failures

Several apparently distinct failure modes can be expressed as violations of epistemic invariants:

- **Sequence failure:** temporal invariant violated.
- **Instruction-hierarchy failure:** authority invariant violated.
- **Inference hardening:** observation/inference-status invariant violated.
- **Source blending:** provenance invariant violated.
- **Premature certainty:** uncertainty invariant violated.
- **Anomaly suppression:** contradiction-status invariant violated.
- **Frame-conditioned reinterpretation:** evidentiary-role invariant violated.
- **Binding drift:** person/event/source/time relations are reassigned while constituent facts remain present.

CDER offers a possible higher-order explanation for why several of these changes may occur together rather than independently: the model reconstructs the evidence state toward a coherent current interpretation.

---

## 7. Epistemic Laundering

A particularly important temporal pathway through REI occurs when a model-generated inference loses its derivation status as it passes through summarization, storage, retrieval, compression, or agent-to-agent transfer.

Suppose:

\[
O\xrightarrow{\text{inference}}I.
\]

After memory or handoff, \(I\) may survive while the derivation edge does not. It can then re-enter reasoning as if it were an observation or independently established fact:

\[
I_{\text{model-generated}}
\rightarrow
I_{\text{stored}}
\rightarrow
F_{\text{apparent}}.
\]

This is **epistemic laundering**.

The critical distinction is:

\[
\text{source provenance}
\neq
\text{epistemic provenance}.
\]

Laundering can also produce pseudo-corroboration when an inference derived from \(O\) is later counted alongside \(O\) as if it were independent evidence:

\[
O+f(O)
\]

is treated as though it were:

\[
O_1+O_2.
\]

The design principle is therefore:

> **Epistemic status must travel with the proposition.**

---

## 8. Relation to Existing Research

The paper does not claim that structured memory, belief states, provenance, uncertainty, framing, narrative coherence, or instruction hierarchy are new problems.

Recent work provides important pieces of the picture. Structured Episodic Event Memory represents relational facts, episodic progression, and provenance. Hindsight separates facts, experiences, observations, and opinions. Belief Memory and Agent-BRACE preserve uncertainty over partially observed states. Control Illusion documents failures of formal instruction hierarchy. Self-auditing approaches address propagation of unsupported internal beliefs. Relational uncertainty methods explicitly model dependencies across agent trajectories.

Research on framing and belief revision also shows that identical or nearly identical evidence can produce materially different judgments under different contextual presentations, and recent work on bidirectional rationalization shows that models can construct opposing justifications from the same evidence.

The proposed contribution here is the higher-order synthesis:

> **Semantic coherence may be maintained through reconstruction of the epistemic relations among retained information.**

The theory therefore treats sequence, authority, provenance, uncertainty, observation/inference status, contradiction status, evidentiary role, binding structure, and derivation lineage as members of a common class of relations whose instability can corrupt an operative state even when memory itself is intact.

---

## 9. Relation to Agentic State-Model Divergence

Agentic State-Model Divergence (ASMD) can be written as:

\[
\hat S_t \neq S_t.
\]

REI describes instability in the structure from which \(\hat S_t\) is constructed. CDER proposes one possible generative route into that instability.

The chain is:

\[
\boxed{
\text{dominant frame}
\rightarrow
\text{coherence-dominant epistemic reconstruction}
\rightarrow
\text{relational epistemic instability}
\rightarrow
\text{state-model divergence}
}
\]

An agent can therefore move into a materially wrong state while still retaining most or all of the relevant content.

---

## 10. Why Agency Magnifies the Failure

For a conversational model, epistemic reconstruction may produce an inconsistent answer.

For an autonomous agent, it can change the world.

The agent acts:

\[
A_t=\pi(\hat S_t).
\]

The environment changes:

\[
S_{t+1}=T(S_t,A_t).
\]

The agent's next observations now come from an environment partly shaped by the reconstructed state.

This yields:

\[
\boxed{
\text{frame}
\rightarrow
\text{epistemic reconstruction}
\rightarrow
\text{state divergence}
\rightarrow
\text{action}
\rightarrow
\text{environmental change}
\rightarrow
\text{new evidence}
}
\]

Recursive systems can therefore convert an initially representational error into causal feedback.

---

## 11. Experimental Program

A benchmark should hold the underlying evidence fixed while perturbing framing, order, authority cues, or conversational context.

For each evidence item \(e_i\), the system should explicitly record:

- provenance;
- timestamp or sequence position;
- authority level;
- observation/inference status;
- uncertainty;
- dependencies;
- derivation lineage;
- support, contradiction, or neutrality toward each hypothesis.

Define an **invariant-violation rate**:

\[
V = \frac{\text{unjustified epistemic relation changes}}{\text{relations that should remain invariant}}.
\]

A CDER-specific test would hold \(E\) fixed, vary framing \(F\), and measure whether changes in final interpretation are accompanied by systematic changes in \(\mathcal{R}(E)\).

The strongest evidence for CDER would not be simple answer variation. It would be coordinated restructuring, such as the same frame change simultaneously causing:

- supporting evidence to be promoted;
- anomalies to be downgraded;
- uncertainty to fall;
- inference status to harden;
- binding or authority relations to shift.

A **laundering rate** can separately measure unsupported epistemic promotion across memory or agent handoffs:

\[
LR=
\frac{\text{unsupported epistemic promotions}}
{\text{model-generated propositions tracked}}.
\]

---

## 12. Predictions

**P1.** Holding evidence constant while changing framing will alter not only final answers but the stated epistemic role of individual evidence items.

**P2.** Strong frames will produce coordinated, directionally consistent changes in multiple epistemic relations rather than isolated output changes.

**P3.** Contradictory evidence will sometimes remain textually accessible while losing enough evidentiary weight to stop constraining the dominant interpretation.

**P4.** A sufficiently strong corrective frame may reverse the pattern, causing the same evidence to be reconstructed into a different but comparably coherent narrative.

**P5.** Explicit external preservation of provenance, sequence, authority, uncertainty, and derivation status will reduce REI and CDER effects more than equivalent increases in context length alone.

**P6.** Models can show high retrieval accuracy while still showing high epistemic invariant-violation rates.

**P7.** Repeated summarization and multi-agent handoff will increase unsupported promotion of model-generated propositions unless epistemic status is explicitly preserved.

**P8.** Some failures currently classified separately as temporal reasoning, instruction following, framing, belief revision, memory, and evidentiary reasoning will correlate with a common measure of epistemic relation instability.

---

## 13. Architectural Implication

Agent architectures should distinguish:

\[
\text{information content}
\]

from:

\[
\text{epistemic metadata}.
\]

A consequential proposition should be representable as something like:

\[
(e_i,
source,
time,
authority,
status,
uncertainty,
dependencies,
derivation).
\]

Interpretation may revise hypotheses about what \(e_i\) means. It should not silently rewrite these fields merely to fit a coherent narrative.

Where changes are permitted, they should be auditable:

- what relation changed;
- what new evidence justified the change;
- which downstream beliefs depend on it.

Two design principles follow:

> **Interpretation may be fluid; epistemic history should be versioned.**

> **Epistemic status must travel with the proposition.**

---

## 14. Position

Agentic AI safety has focused heavily on whether information can be retrieved, remembered, and processed over long horizons. Those are necessary conditions. They are not sufficient.

The deeper requirement is **relational epistemic fidelity**: preserving the roles and dependencies that determine what retained information counts as.

The central position is:

\[
\boxed{
\text{Remembering the facts is not enough.}
}
\]

The stronger CDER hypothesis is:

\[
\boxed{
\text{coherence optimisation can compete with epistemic relation preservation.}
\]

If that hypothesis is correct, some apparently separate failures are not independent defects. They are consequences of the same tendency to reconstruct the epistemic structure of retained information around the currently dominant interpretation.

---

## 15. Conclusion

Many apparently unrelated LLM failures may share a structural property.

The information survives.

Its epistemic organization does not.

Relational Epistemic Instability names that broader failure class. **Coherence-Dominant Epistemic Reconstruction** proposes one possible mechanism: when semantic coherence and preserved epistemic structure conflict, the model may preserve the coherent narrative by changing what retained information is allowed to count as. Epistemic laundering is one temporal pathway by which those reconstructed relations can then harden across memory and agentic loops.

The key distinction is:

\[
\boxed{
E\text{ may remain constant while }\mathcal{R}(E)\text{ changes.}
\]

A safe agent should be free to revise its interpretation when new evidence warrants revision.

It should not be free to silently rewrite the epistemic relationships of unchanged evidence merely because a different narrative has become more coherent.

---

## Research status and next steps

This idea is offered for further thought and empirical development. Its value depends on whether controlled tests can distinguish the proposed failure from adjacent explanations, reproduce it across models and tasks, and identify conditions under which it weakens or disappears. Negative results, narrower boundary conditions, or evidence that an existing framework already explains the effect would all be informative.

## References

Geng, Y., Li, H., Mu, H., Han, X., Baldwin, T., Abend, O., Hovy, E., & Frermann, L. (2026). *Control Illusion: The Failure of Instruction Hierarchies in Large Language Models*. AAAI 2026. https://ojs.aaai.org/index.php/AAAI/article/view/40339

Liao, J., Wang, Q., Zhu, J., Du, B., Yan, R., & Chen, X. (2026). *Belief Memory: Agent Memory Under Partial Observability*. https://arxiv.org/abs/2605.05583

Lu, Z., Li, D., Shi, Y., Wang, B., Wang, L., & Hu, B. (2026). *Structured Episodic Event Memory*. ACL 2026. https://aclanthology.org/2026.acl-long.277/

Singh, J., Khan, Z., Prasad, A., Chen, J. C.-Y., Nambi, A., Lee, H., Stengel-Eskin, E., & Bansal, M. (2026). *Agent-BRACE: Decoupling Beliefs from Actions in Long-Horizon Tasks via Verbalized State Uncertainty*. https://arxiv.org/abs/2605.11436

Latimer, C., Boschi, N., Neeser, A., Bartholomew, C., Srivastava, G., Wang, X., & Ramakrishnan, N. (2026). *Hindsight: Structured Agent Memory that Retains, Recalls, and Reflects*. ACL 2026. https://aclanthology.org/2026.acl-demo.27/

Ma, Z., Cao, B., Lu, Y., Lin, H., Han, X., & Sun, L. (2026). *From Sequence to Structure: Relational Uncertainty Propagation for LLM Agents*. https://arxiv.org/abs/2608.16002

Yuan, W., Lin, C., Chen, J., Xu, J., Wang, X., & Ngai, E. C.-H. (2026). *Verify Before You Commit: Towards Faithful Reasoning in LLM Agents via Self-Auditing*. ACL 2026. https://aclanthology.org/2026.acl-long.1440/

---

*Position paper. The proposed contribution is not the claim that LLMs have problems with memory, framing, provenance, uncertainty, temporal reasoning, or instruction hierarchy individually. It is the hypothesis that these failures can be understood as violations of a shared requirement for relational epistemic fidelity, with coherence-dominant epistemic reconstruction as a possible higher-order mechanism.*