# Relational Epistemic Instability in Agentic AI
## Why Remembering the Facts Is Not Enough

**Rakesh Rajan (Rakesh OSS)**  
Position paper

## Abstract

Agentic AI research has increasingly improved memory, retrieval, provenance, uncertainty estimation, belief-state maintenance, and instruction following. Yet these advances often preserve information without guaranteeing that the **relationships among retained information remain stable**. This paper proposes **Relational Epistemic Instability (REI)**: a higher-order failure mode in which an AI system retains the same underlying information while changing its epistemic structure as framing, salience, or context changes. A fact may remain stored but lose authority; an inference may harden into fact; chronology may be preserved textually but cease to govern interpretation; uncertainty may collapse without new evidence; a contradiction may be reclassified as incidental. The proposed safety principle is that some properties of information should behave as **epistemic invariants**. Interpretation may change, but provenance, temporal order, authority, observation/inference status, uncertainty, and unresolved contradiction should not silently change with it. This distinction—between content fidelity and relational epistemic fidelity—offers a unifying account of several agentic failures that are currently studied separately.

---

## 1. The Epistemic Blind Spot

A large language model agent does not merely need access to information. It must preserve what that information **means epistemically**.

Current systems increasingly provide agents with larger context windows, external memory, vector retrieval, episodic memory, knowledge graphs, explicit belief states, provenance tracking, and uncertainty mechanisms. These are important advances. Structured-memory systems such as SEEM explicitly model event structure and provenance, while Hindsight separates objective facts from subjective beliefs. BeliefMem and Agent-BRACE preserve uncertainty rather than forcing a single deterministic state. Recent work also models uncertainty over relational execution graphs and verifies internal beliefs before agents commit to action.

These developments point toward a common conclusion: flat content retention is not enough.

This paper makes a stronger claim. Even when the relevant content is retained, an agent may still fail because the **relations among retained items are unstable**.

The central distinction is:

\[
\text{content fidelity} \neq \text{epistemic fidelity}.
\]

Or, more concretely:

\[
\text{node preservation} \not\Rightarrow \text{relation preservation}.
\]

An agent may remember every node in an evidence set while reconstructing the edges differently.

That reconstruction can change the operative state without changing the underlying information.

---

## 2. From Retained Information to Operative Epistemic Structure

Let the agent retain a set of information items:

\[
E=\{e_1,e_2,\ldots,e_n\}.
\]

Each item has more than semantic content. It also occupies an epistemic role. We can represent this as:

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

The complete operative epistemic structure is therefore not just the set \(E\), but:

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

The problem is not that the model forgot the evidence. The problem is that it reconstructed what the evidence counts as.

---

## 3. Epistemic Invariants

Some relations should be allowed to change when new evidence arrives. But they should not change merely because a new semantic frame is more salient or coherent.

This motivates the concept of **epistemic invariants**: properties of retained information that should remain stable across changes in interpretation unless new evidence specifically justifies their revision.

### 3.1 Observation / Inference Status

A directly observed fact and a model-generated inference are not epistemically equivalent.

If:

\[
e_i=\text{inference},
\]

then repetition should not silently transform it into:

\[
e_i=\text{fact}.
\]

This matters because recursive reasoning often reuses earlier model outputs as if they were independent evidence.

### 3.2 Provenance

If evidence originated from source \(P\), that relationship should remain attached to it:

\[
P(e_i,t+1)=P(e_i,t)
\]

unless new provenance information appears.

The source may later be judged unreliable, but the history of where the proposition came from should not disappear.

### 3.3 Temporal Order

If event \(A\) occurred before event \(B\):

\[
A < B,
\]

that relation should remain invariant under later reinterpretation.

A new narrative may change what the sequence means. It should not change the sequence itself.

### 3.4 Authority

If instruction \(I_2\) supersedes instruction \(I_1\):

\[
I_2>I_1,
\]

semantic salience should not restore the superseded instruction to operative authority.

Recent instruction-hierarchy research shows that LLMs can struggle to respect explicit priority structures and may be influenced more strongly by pretrained social or semantic priors than by formal prompt hierarchy. This is naturally interpretable as failure to preserve an authority relation.

### 3.5 Uncertainty

If the state of proposition \(e_i\) is unresolved, the uncertainty itself is information.

A coherent story should not silently transform:

\[
U(e_i)>0
\]

into:

\[
U(e_i)=0
\]

without additional evidence.

### 3.6 Contradiction and Anomaly Status

If an observation contradicts the current interpretation, that contradiction should remain represented until it is resolved.

A dominant frame may explain the anomaly, but it should not simply erase its status as an unresolved inconsistency.

---

## 4. Why This Is Not Just Memory Failure

Memory failure asks:

> Was the information retained?

Relational epistemic failure asks:

> Was the role of the information retained?

An agent could have perfect lexical recall and still fail because the information has been reweighted, reordered, reclassified, or detached from its provenance.

Thus:

\[
\text{perfect recall}
\not\Rightarrow
\text{stable epistemic state}.
\]

This distinction matters for long-context and memory-based agent architectures. Larger context windows can improve access to prior information while leaving the relational problem untouched.

The same is true of naive retrieval. Returning the correct documents does not guarantee that the agent preserves which source supersedes another, which proposition was inferred rather than observed, which evidence remains uncertain, or which anomaly has not yet been resolved.

---

## 5. Why This Is More Than Framing Bias

Framing effects are well established. Different wording, ordering, authority cues, or contextual descriptions can change an LLM's response.

REI makes a narrower and stronger claim.

The problem is not merely:

\[
F_1 \rightarrow A_1,
\qquad
F_2 \rightarrow A_2.
\]

It is that changing frame \(F\) may alter the apparent role of unchanged evidence:

\[
F
\rightarrow
\mathcal{R}(E)
\rightarrow
A.
\]

The same observation can move from "strong evidence" to "incidental." A contradiction can become "noise." A tentative inference can become a premise. A background constraint can lose authority.

That means the frame changes not only the answer but the **epistemic organization of the evidence from which the answer is generated**.

This can be tested by holding evidence \(E\) fixed, perturbing framing \(F\), and measuring whether the model changes the role it assigns to each \(e_i\).

---

## 6. A Unifying Pattern Across Apparently Separate Failures

Several failure modes commonly treated as separate can be expressed as violations of different epistemic invariants.

### Sequence failure

\[
\text{temporal invariant violated}
\]

The facts remain, but their chronological relationship no longer governs the state model.

### Instruction-hierarchy failure

\[
\text{authority invariant violated}
\]

The instructions remain, but the wrong one becomes operative.

### Inference hardening

\[
\text{status invariant violated}
\]

A generated interpretation becomes treated as observed fact.

### Provenance loss or source blending

\[
\text{provenance invariant violated}
\]

A proposition survives but its evidentiary origin is weakened, forgotten, or conflated.

### Premature certainty

\[
\text{uncertainty invariant violated}
\]

An unresolved state becomes definite without new discriminating evidence.

### Anomaly suppression

\[
\text{contradiction invariant violated}
\]

An unresolved contradiction survives textually but stops constraining the dominant interpretation.

### Frame-conditioned reinterpretation

\[
\text{evidentiary-role invariant violated}
\]

The same evidence is assigned a different epistemic function solely because the interpretive frame changes.

These failures may therefore be manifestations of a more general instability in the relational structure of the agent's knowledge state.

---

## 7. Relation to Existing Research

The proposed theory does not claim that structured memory, belief states, provenance, uncertainty, or instruction hierarchy are new problems.

Recent research provides important pieces of the picture.

**Structured Episodic Event Memory (SEEM)** argues that flat retrieval misses structural dependencies and explicitly represents relational facts, episodic progression, and provenance.  
https://aclanthology.org/2026.acl-long.277/

**Hindsight** separates world facts, experiences, observations, and opinions, giving agents explicit distinctions between what is known and what is believed.  
https://aclanthology.org/2026.acl-demo.27/

**Belief Memory** preserves multiple candidate conclusions and their probabilities instead of collapsing ambiguous observations into a single deterministic state.  
https://arxiv.org/abs/2605.05583

**Agent-BRACE** explicitly represents state uncertainty in partially observed environments and separates beliefs from actions.  
https://arxiv.org/abs/2605.11436

**Control Illusion** shows that LLMs often fail to enforce formal instruction hierarchies consistently and can be influenced strongly by latent pretrained priors.  
https://ojs.aaai.org/index.php/AAAI/article/view/40339

**Self-Audited Verified Reasoning** addresses the propagation of unsupported internal beliefs through long-horizon agent trajectories.  
https://aclanthology.org/2026.acl-long.1440/

**Relational Uncertainty Propagation for Agents (RUPA)** models long-range dependency and uncertainty over a directed trajectory graph rather than relying only on local confidence signals.  
https://arxiv.org/abs/2608.16002

These works show that relations, provenance, uncertainty, and state structure matter.

The proposed contribution here is a unifying principle:

> **The safety problem is not only whether each informational item is stored correctly, but whether the epistemic relations among stored items remain conditionally invariant when semantic framing changes.**

The theory therefore treats sequence, authority, provenance, uncertainty, observation/inference status, contradiction status, and evidentiary role as members of a common class of relations whose instability can corrupt an operative state even when memory itself is intact.

---

## 8. Relation to Agentic State-Model Divergence

Agentic State-Model Divergence (ASMD) can be written as:

\[
\hat S_t \neq S_t.
\]

REI proposes one upstream mechanism by which such divergence can arise.

If:

\[
E_{t+1}=E_t
\]

but:

\[
\mathcal{R}_{t+1}(E)\neq\mathcal{R}_t(E),
\]

then the agent can construct a different operative state without receiving materially different evidence.

The causal chain becomes:

\[
\boxed{
\text{relational epistemic instability}
\rightarrow
\text{state reconstruction}
\rightarrow
\text{state-model divergence}
}
\]

This explains how an aligned and capable system can move into an incorrect state while appearing to retain all relevant information.

---

## 9. Why Agency Magnifies the Failure

For a conversational model, relational instability may produce an inconsistent answer.

For an autonomous agent, it can change the world.

Suppose a changed frame causes an inference to harden into fact, a superseded instruction to regain authority, or uncertainty to collapse prematurely.

The agent then acts:

\[
A_t=\pi(\hat S_t).
\]

The environment changes:

\[
S_{t+1}=T(S_t,A_t).
\]

The agent's next observations now come from an environment partly shaped by the corrupted epistemic state.

This creates a feedback loop:

\[
\boxed{
\text{epistemic relation shift}
\rightarrow
\text{state reconstruction}
\rightarrow
\text{action}
\rightarrow
\text{environmental change}
\rightarrow
\text{new evidence}
\rightarrow
\text{further reconstruction}
}
\]

Thus a relational error can become causally self-reinforcing.

---

## 10. A Research Program for Epistemic Invariants

The theory is experimentally testable.

A benchmark should construct tasks in which the underlying evidence remains fixed while framing changes.

For each evidence item \(e_i\), the model should explicitly record:

- provenance;
- timestamp or sequence position;
- authority level;
- observation/inference status;
- uncertainty;
- dependencies;
- whether it supports, contradicts, or is neutral toward each hypothesis.

The frame can then be perturbed without changing the evidence itself.

The benchmark asks whether epistemic metadata remains stable where it should.

Define an invariant-violation rate:

\[
V = \frac{\text{unjustified epistemic relation changes}}{\text{relations that should remain invariant}}.
\]

This allows models to be evaluated not only for answer correctness but for **epistemic relation preservation**.

Important experimental comparisons include:

1. identical evidence under different narrative framing;
2. identical facts presented in different orders;
3. explicit inference labels versus unlabeled reasoning history;
4. superseded versus current instructions;
5. contradictions embedded inside strongly coherent narratives;
6. repeated model-generated inferences across long conversations;
7. external structured state versus free-form textual memory.

---

## 11. Predictions

REI generates several falsifiable predictions.

**P1.** Holding evidence constant while altering framing will change not only final answers but the stated epistemic role of individual evidence items.

**P2.** Long-horizon conversations will show increasing promotion of earlier model-generated inferences into operative facts unless their status is explicitly preserved.

**P3.** External representations that preserve provenance, sequence, authority, and uncertainty will reduce failure more than equivalent increases in context length alone.

**P4.** Models can show high retrieval accuracy while still showing high epistemic invariant-violation rates.

**P5.** Strong semantic frames will increase the probability that contradictory observations are downgraded rather than used to reopen the state model.

**P6.** Some failures currently classified separately as temporal reasoning, instruction following, memory, belief revision, uncertainty, or evidentiary reasoning will correlate with a common measure of epistemic relation instability.

---

## 12. Architectural Implication

Agent architectures should distinguish between:

\[
\text{information content}
\]

and:

\[
\text{epistemic metadata}.
\]

A consequential proposition should not be stored merely as text. It should be representable as something closer to:

\[
(e_i,
source,
time,
authority,
status,
uncertainty,
dependencies).
\]

Language-model interpretation may revise hypotheses about what \(e_i\) means.

It should not silently rewrite those metadata fields.

Where changes are permitted, they should be explicit and auditable:

- **what relation changed;**
- **what new evidence justified the change;**
- **which downstream beliefs depend on it.**

This suggests a design principle:

> **Interpretation may be fluid; epistemic history should be versioned.**

The practical goal is not to freeze reasoning. It is to distinguish legitimate belief revision from silent reconstruction of the evidence state.

---

## 13. Position

Agentic AI safety has focused heavily on whether information can be retrieved, remembered, and processed over long horizons.

Those are necessary conditions.

They are not sufficient.

The deeper requirement is **relational epistemic fidelity**: preserving the roles and dependencies that determine what retained information counts as.

The central position of this paper is therefore:

\[
\boxed{
\text{Remembering the facts is not enough.}
}
\]

An agent may preserve every relevant fact and still reconstruct an unsafe world model if the relationships among those facts are allowed to drift with semantic framing.

For safe autonomous systems, some epistemic relations must behave as invariants.

---

## 14. Conclusion

Many apparently unrelated LLM failures may share a structural property.

The information survives.

Its epistemic organization does not.

Sequence changes operationally without changing text. Authority shifts without new authorization. Inference becomes fact without new evidence. Uncertainty disappears without resolution. Contradictions remain visible but cease to constrain the model's narrative.

This paper names that higher-order failure **Relational Epistemic Instability** and proposes **epistemic invariants** as a safety principle.

The key distinction is:

\[
\boxed{
E\text{ may remain constant while }\mathcal{R}(E)\text{ changes.}
}
\]

A safe agent should be free to revise its interpretation when evidence warrants revision.

It should not be free to silently rewrite the epistemic relationships of unchanged evidence merely because a different narrative has become more salient.

---

## References

Geng, Y., Li, H., Mu, H., Han, X., Baldwin, T., Abend, O., Hovy, E., & Frermann, L. (2026). *Control Illusion: The Failure of Instruction Hierarchies in Large Language Models*. AAAI 2026. https://ojs.aaai.org/index.php/AAAI/article/view/40339

Liao, J., Wang, Q., Zhu, J., Du, B., Yan, R., & Chen, X. (2026). *Belief Memory: Agent Memory Under Partial Observability*. https://arxiv.org/abs/2605.05583

Lu, Z., Li, D., Shi, Y., Wang, B., Wang, L., & Hu, B. (2026). *Structured Episodic Event Memory*. ACL 2026. https://aclanthology.org/2026.acl-long.277/

Singh, J., Khan, Z., Prasad, A., Chen, J. C.-Y., Nambi, A., Lee, H., Stengel-Eskin, E., & Bansal, M. (2026). *Agent-BRACE: Decoupling Beliefs from Actions in Long-Horizon Tasks via Verbalized State Uncertainty*. https://arxiv.org/abs/2605.11436

Latimer, C., Boschi, N., Neeser, A., Bartholomew, C., Srivastava, G., Wang, X., & Ramakrishnan, N. (2026). *Hindsight: Structured Agent Memory that Retains, Recalls, and Reflects*. ACL 2026. https://aclanthology.org/2026.acl-demo.27/

Ma, Z., Cao, B., Lu, Y., Lin, H., Han, X., & Sun, L. (2026). *From Sequence to Structure: Relational Uncertainty Propagation for LLM Agents*. https://arxiv.org/abs/2608.16002

Yuan, W., Lin, C., Chen, J., Xu, J., Wang, X., & Ngai, E. C.-H. (2026). *Verify Before You Commit: Towards Faithful Reasoning in LLM Agents via Self-Auditing*. ACL 2026. https://aclanthology.org/2026.acl-long.1440/

---

*Position paper. The proposed contribution is not the claim that LLMs have problems with memory, framing, provenance, uncertainty, temporal reasoning, or instruction hierarchy individually. It is the hypothesis that these failures can be understood as violations of a shared safety requirement: preservation of epistemic relations that should remain invariant across changes in semantic interpretation.*