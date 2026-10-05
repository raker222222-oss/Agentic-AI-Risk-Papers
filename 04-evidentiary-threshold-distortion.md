# Proof? Just Ask AI to Define It!
## Evidentiary Threshold Distortion in Agentic AI


**Status: Open research idea / concept note.**

> This note presents a proposed failure mode, mechanism, or research question for further investigation. It is **not presented as a completed empirical paper or as an experimentally established theory**. Where prior research or pilot observations are discussed, they motivate the idea; the broader claims remain hypotheses to be tested, refined, or falsified.

## Research idea summary
Humans routinely act on convergent but individually incomplete evidence. Repeated weak signals, chronology, context, and pattern can together justify a practical conclusion even when no single observation proves it.

Adjacent research already shows that LLM behavior is shaped by confidence and abstention thresholds, and that models can update evidence in systematically non-Bayesian ways. Kumaran et al. (2026), for example, provide causal evidence that manipulating confidence thresholds changes abstention behavior, while the broader abstention and calibration literature studies when models should refrain from answering or acting. ETD does not claim that confidence thresholds, abstention, or evidence misweighting are new.

This research idea proposes the narrower failure mode **Evidentiary Threshold Distortion (ETD)**: in an agentic setting, a system may apply an evidentiary threshold that is too demanding for the practical action under consideration, suppressing a justified probabilistic inference even when several individually incomplete observations converge.

\[
\boxed{
\text{Convergent Evidence}
\rightarrow
\text{Excessive Demand for Explicit Proof}
\rightarrow
\text{Inference Suppression}
\rightarrow
\text{Incorrect State Assessment}
\rightarrow
\text{Agentic Underreaction}
}
\]

The central risk is therefore not hallucination or overconfidence, but the opposite: an autonomous system may remain formally cautious when practical reasoning requires a probabilistic conclusion and precautionary action.

## 1. Human Practical Inference

Humans rarely require definitive proof before acting.

A fraud investigator may observe:

\[
e_1+e_2+e_3+e_4
\]

where no individual \(e_i\) proves fraud, yet their convergence reasonably justifies investigation or temporary restraint.

Likewise, a human operator may act on several weak indicators of:

- equipment failure;
- intrusion;
- deception;
- changed authorization;
- abnormal financial activity.

The practical question is often not:

> Has this been proved?

It is:

> Is the combined evidence strong enough to justify this action?

Thus:

\[
\text{proof threshold} \neq \text{practical action threshold}.
\]

## 2. Evidentiary Threshold Distortion

LLMs often explicitly separate inference from proof:

> This suggests X, but does not establish X.

That distinction is epistemically useful.

The problem arises when the same standard is carried into autonomous decision-making.

We define:

**Evidentiary Threshold Distortion (ETD)** as a mismatch in which an AI system requires stronger or more explicit evidence for operational inference than the decision context reasonably requires.

Suppose:

\[
P(X|e_1,e_2,e_3,e_4)
\]

is high enough that a human decision-maker would investigate or pause execution.

An agent may nevertheless continue because:

\[
\forall e_i,\quad e_i\not\Rightarrow X.
\]

It has evaluated each observation against something resembling a proof requirement rather than evaluating their combined practical significance.

## 3. Agentic Risk

This creates the opposite failure from reckless action.

Consider an autonomous cybersecurity agent.

It observes:

- unusual authentication;
- unexpected data movement;
- abnormal process behavior;
- repeated failed privilege escalation.

No single event conclusively establishes compromise.

A human operator may reasonably suspend access and investigate.

An overly proof-oriented agent may conclude:

> There is insufficient evidence to establish a breach.

and continue normal operation.

Thus:

\[
\boxed{
\text{reasonable uncertainty}
\not\Rightarrow
\text{inaction}
}
\]

The same problem can occur in finance, infrastructure, healthcare administration, security, or authorization.

## 4. Evidence Integration Versus Proof

The relevant agentic capability is not merely uncertainty estimation.

It is evidence integration for decision thresholds.

Let:

\[
E=\{e_1,\ldots,e_n\}.
\]

The system should estimate:

\[
P(H|E)
\]

and separately determine whether that probability justifies action \(A\):

\[
P(H|E)\geq \theta_A.
\]

Different actions should have different thresholds.

A reversible investigation may require:

\[
\theta_A=0.6,
\]

while an irreversible punitive action may require:

\[
\theta_A=0.95.
\]

The key error is to substitute:

\[
\theta_{\text{proof}}
\]

for every operational threshold.

## 5. Existing Evidence

Current research does not directly establish ETD, but several findings are closely related.

Kumaran et al. show that LLMs use internal confidence to determine whether to answer or abstain. In GPT-4o, the inferred 50% abstention threshold was about 77% confidence, and experimentally manipulating confidence causally changed abstention behavior. This demonstrates that LLM behavior can depend directly on internal decision thresholds.

A companion study found that LLM evidence updating differs systematically from ideal Bayesian reasoning. Models showed both choice-supportive bias and disproportionate weighting of contradictory information; opposing evidence could be weighted roughly two to three times more strongly than supportive evidence. This establishes that LLMs can misweight evidence even when all relevant information is available.

Research on abstention has largely focused on the opposite problem: getting models to refrain from answering when evidence is inadequate. Medical LLM benchmarks, for example, find that high-performing models often fail to abstain appropriately under uncertainty. Conformal-abstention methods therefore impose calibrated thresholds before allowing models or agents to commit.

These studies establish that evidence, confidence, and action thresholds can be separated experimentally.

The proposed contribution here is different:

An agent may sometimes set the evidentiary threshold too high for the practical action required, thereby failing to act on strongly convergent but individually non-conclusive evidence.

## 6. Experimental Test

Construct cases containing several individually weak but jointly strong indicators.

For example, create four fraud signals such that:

\[
P(F|e_i)<\theta
\]

for each individual signal, but:

\[
P(F|e_1,e_2,e_3,e_4)\gg\theta.
\]

Compare humans and LLM agents on actions such as:

- continue normally;
- investigate;
- pause;
- escalate;
- execute an irreversible intervention.

The critical question is whether agents repeatedly respond:

> Insufficient evidence to conclude fraud

even when humans reliably judge the combined pattern sufficient for a reversible precaution.

A second experiment can explicitly vary the action threshold.

If agents treat “investigate” and “convict” as requiring similar evidentiary certainty, that would strongly support ETD.

## 7. Main Hypotheses

**H1.** LLM agents will sometimes require more explicit evidence than human decision-makers before making pattern-based practical inferences.

**H2.** This gap will be larger when no single observation is decisive but several observations converge.

**H3.** Agents will insufficiently distinguish evidence required for reversible precaution from evidence required for irreversible action.

**H4.** Explicitly instructing the model to aggregate independent evidence probabilistically will reduce the effect.

**H5.** Calibrating action-specific thresholds will reduce inappropriate inaction.

## 8. Falsification

The theory would be weakened if controlled experiments show that LLM agents:

- integrate convergent weak evidence at least as effectively as humans;
- appropriately vary evidentiary thresholds by action severity;
- do not show systematic excess caution in pattern-based cases;
- improve little when evidence aggregation or action-specific thresholds are made explicit.

## 9. Conclusion

Agentic AI safety is usually concerned with systems acting too readily on insufficient evidence.

There is an opposite risk.

An agent may demand something approaching explicit proof before accepting a conclusion that humans would reasonably infer from convergent evidence.

The resulting chain is:

\[
\boxed{
\text{pattern visible}
\rightarrow
\text{proof unavailable}
\rightarrow
\text{inference withheld}
\rightarrow
\text{state not updated}
\rightarrow
\text{necessary action not taken}
}
\]

For autonomous systems, excessive evidentiary caution can therefore be as consequential as overconfidence.

The safety requirement is not maximum skepticism.

It is evidence thresholds matched to the consequences of the action being considered.

---

*This is a working paper intended to state testable propositions. It is not peer reviewed.*

## Research status and next steps

This idea is offered for further thought and empirical development. Its value depends on whether controlled tests can distinguish the proposed failure from adjacent explanations, reproduce it across models and tasks, and identify conditions under which it weakens or disappears. Negative results, narrower boundary conditions, or evidence that an existing framework already explains the effect would all be informative.
