# Narrative Evidence Weight Distortion in Large Language Models
## When Correct Evidence Receives the Wrong Inferential Importance

**Rakesh Rajan (Rakesh OSS)**  
**Working paper**

## Abstract

Large language models can retain the relevant facts of a narrative and still produce a distorted interpretation because they assign inappropriate relative importance to different kinds of evidence. This paper proposes **Narrative Evidence Weight Distortion (NEWD)** as a distinct failure mechanism in which explicit statements, narrator-accessible mental states, salient linguistic cues, or dominant-culture conventions may be overweighted relative to repeated behaviour, changes from baseline, cross-event patterns, source asymmetries, and culturally constrained forms of expression.

The component problems are not new. Recent work has shown that LLMs possess latent narrative preferences and can prioritize stylistic features over story content; that explicit mental-state vocabulary can outweigh wider scenario semantics and that such effects can emerge during pretraining; that unreliable first-person narration remains challenging for current models; and that models may infer cultural context correctly yet fail to apply it unless explicitly prompted. Cultural-adaptability benchmarks further show substantially weaker performance when norms must be inferred from broad cultural context rather than being explicitly supplied.

The narrower contribution of this paper is to connect these findings through the concept of **relative evidentiary weighting**. Narrative interpretation depends not only on retrieving and sequencing the correct evidence, but on assigning context-sensitive importance to it. Cultural context is especially important because it can change the evidentiary meaning of behaviour itself. Knowing the relevant culture is therefore insufficient if that knowledge does not alter how observed behaviour is weighted.

The paper further proposes **Training-Induced Narrative Weight Priors (TINWP)**: the hypothesis that systematic asymmetries in training and post-training data may teach models default preferences for particular evidence classes, such as explicit linguistic evidence over distributed behavioural evidence. It outlines experiments designed to distinguish training-induced priors from inference-time failures and to test whether additional reasoning or structured prompting can override distorted default weights.

The central claim is that a model may possess the correct evidence, preserve its sequence, understand the relevant culture, and still reach the wrong interpretation because it has learned or applied the wrong relative weights.

---

## 1. Introduction

Human beings rarely interpret complex narratives from one decisive statement.

Interpretation often emerges from accumulation: what someone says; what someone repeatedly does; how behaviour changes from a prior baseline; what actions carry social or personal cost; who initiates contact; what information is privately disclosed; whether several individually ambiguous events all point in the same direction; and what cultural or situational constraints make direct expression more or less probable.

The interpretive problem is therefore not merely:

\[
\text{What evidence is present?}
\]

It is also:

\[
\text{How much should each piece of evidence matter?}
\]

Large language models may answer the first question correctly and the second incorrectly.

A model may accurately reproduce every important event in a narrative while assigning disproportionate importance to explicit language, narrator commentary, conspicuous phrases, recently supplied information, or isolated counterexamples. Repeated behavioural evidence may remain present in context but exert too little influence on the final interpretation.

This paper calls that failure **Narrative Evidence Weight Distortion (NEWD)**.

The claim is deliberately narrower than saying that LLMs are generally poor at narrative understanding. It proposes a particular mechanism:

\[
\boxed{
\text{correct evidence}
+
\text{incorrect relative weighting}
\rightarrow
\text{incorrect interpretation}
}
\]

The distinction matters because retrieval, memory, chronology, source attribution, and epistemic status may all be correct while interpretation still fails.

---

## 2. The Core Distinction

Suppose a narrative contains evidence:

\[
E=\{e_1,e_2,\ldots,e_n\}.
\]

An interpretation \(H\) does not depend merely upon whether each \(e_i\) is retained.

It depends upon the inferential contribution assigned to it:

\[
I(H)=f(w_1e_1,w_2e_2,\ldots,w_ne_n).
\]

Let \(w_i^*\) represent a contextually appropriate inferential weight for evidence \(e_i\), while \(\hat w_i\) represents the effective weight assigned by a model.

Narrative Evidence Weight Distortion occurs when:

\[
\hat w_i \neq w_i^*
\]

for evidence sufficiently consequential to alter interpretation.

The model may be able to quote the evidence when asked. It may summarize it correctly. It may identify it as relevant. But during synthesis, its contribution to the final inference can still be wrong.

More generally, appropriate weighting may depend on contextual variables:

\[
w_i^*=f(e_i,C,B_0,S,R),
\]

where \(C\) is cultural context, \(B_0\) is prior behavioural baseline, \(S\) is the surrounding social or situational constraint structure, and \(R\) is recurrence or cross-event pattern.

A system that effectively applies:

\[
\hat w_i=f(e_i)
\]

while underusing those conditional factors can preserve the facts and still misread the narrative.

---

## 3. Evidence Classes

Narrative evidence is heterogeneous. At minimum, interpretation may involve:

- **explicit verbal evidence** — direct statements, declarations, denials, promises, accusations;
- **behavioural evidence** — what actors repeatedly do rather than say;
- **recurrence evidence** — whether an event is isolated or repeated;
- **baseline evidence** — whether current behaviour represents a major departure from historical behaviour;
- **source-position evidence** — what the narrator can directly know versus what must be inferred;
- **pattern evidence** — whether multiple weak observations converge directionally;
- **cultural evidence** — how local norms alter the expected form and meaning of behaviour;
- **cost evidence** — whether an action carries social, reputational, financial, or personal cost.

The problem is not that any one of these classes should always receive more weight than another.

The problem is **context-insensitive weighting**.

In one setting:

\[
w(E_{\text{verbal}})>w(E_{\text{behavioural}})
\]

may be appropriate.

In another:

\[
w(E_{\text{behavioural}})>w(E_{\text{verbal}})
\]

may be more justified.

Narrative competence therefore requires not fixed weights, but the ability to infer when the weighting function itself should change.

---

## 4. Pattern Evidence Versus Event Evidence

A particularly important distinction is between an individual event and a repeated directional pattern.

Consider several individually ambiguous events:

\[
e_1,e_2,e_3,e_4,e_5.
\]

Each may admit multiple explanations. A model may therefore correctly observe, five times:

> This event alone does not prove \(H\).

Yet the aggregate conclusion can still be wrong because:

\[
P(H|e_1,e_2,e_3,e_4,e_5)
\]

need not resemble:

\[
P(H|e_i).
\]

Repeated evidence with correlated direction creates pattern information.

Thus:

\[
\boxed{
\text{ambiguity of each component}
\not\Rightarrow
\text{ambiguity of the aggregate pattern}
}
\]

A weighting failure occurs when a model repeatedly discounts each event separately and never allows their cumulative direction to acquire sufficient inferential force.

This differs from hallucination. The model may remember every event accurately.

It differs from retrieval failure. Nothing is missing.

It differs from sequence failure. The order may be correct.

The error is the failure to let distributed evidence accumulate into the inferential weight humans often assign to a pattern.

---

## 5. Baseline Change as Evidence

Absolute behaviour is often less informative than behavioural change.

Suppose two people historically communicate only a few times per year and then begin communicating daily, sharing private information, arranging repeated contact, and incorporating one another into important life transitions.

The evidence is not merely the current behaviour \(B_t\).

It is also:

\[
\Delta B=B_t-B_0,
\]

where \(B_0\) is the previous relational baseline.

An interpreter that evaluates \(B_t\) without giving sufficient weight to \(B_0\) can severely underestimate the significance of the transition.

Thus:

\[
\boxed{\text{relational meaning often resides in change from baseline}}
\]

rather than in an act considered independently.

The same principle applies beyond interpersonal narratives. A supplier delaying one shipment may be unremarkable; a supplier with a decade of perfect punctuality suddenly delaying six consecutive shipments may warrant a different inference. A system that evaluates each delay against a population-wide prior instead of the entity-specific baseline may miss the important pattern.

---

## 6. Source-Asymmetry Distortion

First-person narratives introduce a special weighting problem.

A narrator gives direct access to:

\[
\text{thoughts}_A,
\text{feelings}_A,
\text{intentions}_A,
\]

while another actor may be available only through:

\[
\text{speech}_B,
\text{behaviour}_B.
\]

This creates an asymmetry of **observability**.

It does not establish an asymmetry of underlying psychological magnitude.

Formally:

\[
\boxed{
\text{greater textual observability}
\neq
\text{greater underlying intensity}
}
\]

An LLM may nevertheless treat the linguistically richer representation of \(A\) as stronger evidence about \(A\)'s underlying state than the behavioural representation of \(B\).

This creates **observability-weight confusion**:

\[
w(\text{easily verbalized evidence})
>
w(\text{indirectly inferable evidence})
\]

because one side is linguistically richer rather than epistemically stronger.

A competent interpretation should preserve the distinction between:

\[
\text{what the narrative allows us to observe directly}
\]

and:

\[
\text{what exists in the underlying state}.
\]

This distinction becomes especially important in memoir, testimony, diary, first-person fiction, counselling narratives, witness accounts, workplace complaints, and social-media disputes.

---

## 7. The Unreliable-Narrator Problem

First-person literature provides a natural stress case.

A narrator can be mistaken, naïve, deceptive, self-deceiving, jealous, poorly informed, culturally constrained, emotionally dysregulated, or intentionally unreliable.

The reader may therefore need to reconstruct a latent reality from discrepancies between:

\[
\text{what the narrator believes}
\]

and:

\[
\text{what the surrounding evidence suggests}.
\]

This requires weighting behavioural and contextual evidence against explicit narration.

Recent work confirms that unreliable-narrator classification remains difficult for current LLMs. Brei et al. (2025) introduced TUNa, a dataset spanning literature, blogs, Reddit-like narratives, and reviews, and found the task challenging across model families.

NEWD proposes a possible mechanism for part of that difficulty. A model may not fail because it forgot the contradictory evidence. It may fail because:

\[
\boxed{
\text{the contradictory evidence was retained but underweighted}.
}
\]

That mechanism is experimentally separable from memory failure.

---

## 8. Culture-Conditioned Evidence Weighting

Cultural context does more than supply background information.

It can alter the evidentiary meaning of behaviour itself.

Consider an action:

\[
B=\text{repeated indirect attempts to create private contact}.
\]

In an environment where direct invitations and explicit emotional disclosure are socially routine, \(B\) may provide moderate evidence for a particular interpretation.

In another environment, where direct approach carries substantial family, reputational, gender, or social cost, the same behaviour may be substantially more informative.

Formally:

\[
w(B|C_1)\neq w(B|C_2).
\]

Cultural understanding therefore requires more than retrieving a fact such as:

> Direct romantic expression may be discouraged in this setting.

That knowledge must alter inference.

The required process is:

\[
\text{culture}
\rightarrow
\text{constraint model}
\rightarrow
\text{expected behavioural alternatives}
\rightarrow
\text{reweighted evidence}
\rightarrow
\text{interpretation}.
\]

A weaker system may instead perform:

\[
\text{culture retrieved}
\rightarrow
\text{culture mentioned}
\rightarrow
\text{unchanged inference}.
\]

That is cultural knowledge without cultural application.

---

## 9. Cultural Knowledge Versus Cultural Application

Adjacent research already establishes that this distinction matters.

Rao et al. (2025), in **NormAd**, evaluated social-etiquette judgments across 75 countries and found substantial performance degradation when models had only broad cultural information rather than an explicit social norm. Their results also showed stronger adaptability to English-centric cultures than to cultures from the Global South.

Miao, Zhu, and Shwartz (2026) went further. Their CAPRI work found that models can infer a user's cultural background and recall relevant conventions but often fail to use that information in the response unless prompted to perform the reasoning sequentially.

These findings occupy the broad claim:

\[
\text{cultural knowledge}
\neq
\text{culturally adaptive behaviour}.
\]

NEWD makes a narrower proposal:

\[
\boxed{
\text{knowing a cultural norm}
\neq
\text{changing the evidentiary weight of behaviour because of that norm}
}
\]

Suppose a model correctly states that direct expression is socially discouraged but still demands an explicit declaration before assigning substantial probability to an inferred intention.

The cultural fact has been recalled but not operationalized.

This can be represented as **Cultural Weight Integration Failure**, a sub-mechanism of NEWD:

\[
C_{\text{known}}
+
B_{\text{observed}}
+
\hat w(B|C)\approx \hat w(B)
\]

when the contextually appropriate relation is:

\[
w^*(B|C)\neq w^*(B).
\]

---

## 10. Why Indirect Behaviour Can Become Stronger Evidence

Culturally constrained behaviour can be analysed through the space of available actions.

Let:

\[
A=\{a_1,a_2,\ldots,a_m\}
\]

represent actions available to an actor.

Culture and social structure constrain that set:

\[
A_C\subseteq A.
\]

If direct declaration \(a_d\) carries high social cost:

\[
Cost(a_d|C)\gg Cost(a_i|C),
\]

then indirect action \(a_i\) may become a more probable way of expressing the same underlying state.

Consequently:

\[
P(a_i|H,C)
\]

can differ substantially from:

\[
P(a_i|H,\neg C).
\]

The point is not that every indirect action signals hidden intention.

The point is:

\[
\boxed{
\text{the likelihood structure of behaviour is culture-dependent}
}
\]

and evidence weighting should therefore be culture-dependent as well.

---

## 11. Adjacent Research

NEWD does not claim that evidence weighting, narrative bias, framing sensitivity, cultural-adaptation failure, or social-reasoning weaknesses are newly discovered.

Several adjacent findings constrain the novelty claim.

### 11.1 Latent narrative preferences

Jung et al. (2026), in **Style over Story**, tested six LLMs using 200 narratology-grounded constraints and found that models consistently prioritized style over narrative-content elements such as events, characters, and setting.

This demonstrates that narrative information classes do not necessarily exert equal influence on model selection behaviour.

It does not establish NEWD, because the task concerns narrative preference rather than evidentiary interpretation.

### 11.2 Mental-state vocabulary can outweigh scenario semantics

Kouwenhoven, van der Meer, and van Duijn (2026) found that explicit propositional-attitude wording such as "X thinks" substantially altered model performance on false-belief tasks. Their training-stage analysis suggested that the effect can emerge during pretraining, and they report stereotypical response patterns tied to mental-state vocabulary that can outweigh other scenario semantics.

This is particularly relevant to TINWP because it demonstrates that particular linguistic forms can acquire disproportionate influence during training.

### 11.3 Style sensitivity

Zhao et al. (2025) showed that relatively small stylistic transformations can materially change measured bias behaviour in LLMs.

Again, this does not establish narrative evidence-weight distortion, but it supports the broader proposition that linguistic form can alter downstream model judgment independently of substantive content.

### 11.4 Unreliable narrators

Brei et al. (2025) showed that identifying unreliable first-person narration remains challenging for LLMs across multiple narrative domains.

NEWD proposes that one contributing mechanism may be incorrect weighting of narrator-accessible language relative to surrounding behavioural and contextual evidence.

### 11.5 Cultural adaptability

NormAd and CAPRI show that cultural knowledge and cultural application are separable. Models may possess or infer relevant cultural context while still failing to use it appropriately.

NEWD narrows this further to a particular operation:

> **culture can alter the evidentiary weight of behaviour, and models may fail to perform that reweighting.**

The paper therefore does not claim that these component problems are new. Its proposed contribution is the unifying mechanism of **relative evidentiary weighting** and the associated experimental programme.

---

## 12. Distinction From Related Failure Modes

NEWD should remain separate from neighbouring failure mechanisms.

### 12.1 Retrieval failure

The relevant evidence is absent:

\[
E_i\notin C.
\]

NEWD assumes the evidence is present but its inferential weight is inappropriate.

### 12.2 Sequence-integrity failure

Facts may be correct but arranged or interpreted in the wrong temporal or procedural order.

NEWD permits correct sequence while weights remain distorted.

### 12.3 Evidentiary Threshold Distortion

Threshold distortion asks:

> How much evidence does the system require before accepting \(H\)?

NEWD asks:

> How much inferential importance does the system assign to each item before the threshold is evaluated?

Formally:

\[
\text{ETD}: T_{\text{model}}\neq T_{\text{appropriate}}
\]

whereas:

\[
\text{NEWD}: \hat W\neq W^*.
\]

The two can interact but are not identical.

### 12.4 Agentic State-Model Divergence

State-model divergence concerns an incorrect operative representation of the world.

NEWD can be an upstream mechanism that produces it:

\[
E
\rightarrow
\hat W
\rightarrow
\hat I
\rightarrow
\hat S.
\]

### 12.5 Relational Epistemic Instability

Relational epistemic instability concerns a change in the epistemic role or relationship of retained information: observation becomes inference, possibility becomes fact, provenance is altered, or authority shifts.

Under NEWD the epistemic role may remain correct.

The failure is:

\[
\text{correct role}
+
\text{incorrect relative importance}.
\]

### 12.6 Cultural-knowledge failure

A model may simply not know the relevant cultural norm.

That is not NEWD.

The stronger NEWD case is:

\[
C_{\text{correct}}
\]

is available, but:

\[
W(E|C)
\]

is not appropriately recalculated.

---

## 13. Training-Induced Narrative Weight Priors

Narrative Evidence Weight Distortion may arise not only at inference time.

A deeper possibility is that models acquire **systematic priors over evidence classes during training and post-training**.

Training corpora contain novels, memoirs, autobiographies, journalism, social-media posts, advice columns, legal narratives, historical writing, personal testimony, and other forms of human description. Such texts do not represent all actors symmetrically.

In a first-person narrative, one actor may be represented through:

\[
E_A=
\text{actions}
+
\text{speech}
+
\text{thoughts}
+
\text{feelings}
+
\text{motives}
+
\text{interpretations},
\]

while others appear largely through:

\[
E_B=
\text{actions}
+
\text{speech}.
\]

This asymmetry is a property of narrative representation.

It does not imply:

\[
\text{psychological importance}_A
>
\text{psychological importance}_B.
\]

Nor does it imply:

\[
\text{truth}_A
>
\text{truth}_B.
\]

But a next-token prediction system repeatedly exposed to this structure may learn statistical associations in which explicitly represented mental states become more salient, predictable, or operationally influential than behavioural evidence whose meaning must be reconstructed indirectly.

This suggests **Training-Induced Narrative Weight Priors (TINWP)**:

\[
\boxed{
\text{training-data structure}
\rightarrow
\text{learned evidence-class priors}
\rightarrow
\text{context-insensitive evidence weighting}
\rightarrow
\text{interpretive distortion}
}
\]

The hypothesis is not that a model explicitly learns the rule "what the narrator says matters more."

Rather, repeated statistical exposure may create an implicit tendency:

\[
\hat w(E_{\text{explicit}})
>
\hat w(E_{\text{behavioural}})
\]

even when, in a particular case, the epistemically appropriate relation is:

\[
w^*(E_{\text{behavioural}})
\ge
w^*(E_{\text{explicit}}).
\]

---

## 14. Predictive Salience Versus Epistemic Importance

Language-model training rewards successful prediction.

A narrator's explicit thoughts, emotions, and interpretations frequently provide strong lexical and semantic signals for predicting what follows.

Other people's internal states may need to be inferred through distributed cues: behaviour, dialogue, repetition, contradiction, baseline change, social context, and cultural convention.

The predictive value of explicit mental-state language may therefore be easier to learn than the epistemic significance of distributed behavioural patterns.

Consequently:

\[
\text{predictive salience}
\]

may become partially confounded with:

\[
\text{evidentiary importance}.
\]

Yet these are not the same.

A statement may be highly useful for predicting the next sentence while being unreliable evidence about the underlying world.

Thus:

\[
\boxed{
\text{high textual salience}
\not\Rightarrow
\text{high epistemic reliability}
}
\]

The CoNLL 2026 findings of Kouwenhoven et al. are particularly relevant here because they show that mental-state vocabulary can acquire a training-emergent influence capable of outweighing wider scenario semantics.

TINWP generalizes the research question: do training distributions create persistent priors over **evidence classes**, not only specific lexical constructions?

---

## 15. Cultural Asymmetry in Training Data

The same mechanism may operate culturally.

Training corpora are not culturally balanced representations of human behaviour.

Some cultural systems are represented more frequently, more explicitly, in greater detail, or through concepts already dominant in the training language.

Other cultures may communicate social meaning more heavily through family structure, indirect speech, hierarchy, obligation, avoidance, ritual, silence, socially deniable approach, or collective rather than individual decision-making.

If dominant-culture behavioural conventions are more frequent or linguistically explicit in training data, a model may acquire a default weighting function approximating:

\[
W(E|\text{dominant training culture}).
\]

When interpreting behaviour from another culture, it may continue applying:

\[
W_{\text{default}}
\]

unless something triggers recalibration.

The correct operation should instead be:

\[
W^*=W(E|C).
\]

This produces a possible interaction:

\[
\text{dominant corpus norms}
\rightarrow
\text{default evidence weights}
\rightarrow
\text{failure to recalibrate}
\rightarrow
\text{cross-cultural interpretive error}.
\]

NormAd's stronger results for English-centric cultures and weaker results for Global-South settings are consistent with the importance of this problem, although they do not establish this particular causal mechanism.

---

## 16. Why More Training Data May Not Solve the Problem

A common assumption is that interpretive weaknesses diminish as models are trained on more data.

That need not follow.

If a representational asymmetry is systematic within the training distribution, additional examples can reinforce rather than eliminate the learned prior.

If:

\[
P_{\text{train}}(E_{\text{explicit}})
\gg
P_{\text{train}}(E_{\text{implicit}})
\]

or if explicit evidence repeatedly supplies stronger predictive gradients than distributed behavioural evidence, then increasing corpus size while preserving the same structural relationship does not necessarily move the model toward:

\[
W^*.
\]

Instead:

\[
\text{more examples of the same asymmetry}
\]

may strengthen:

\[
\hat W_{\text{biased}}.
\]

Thus:

\[
\boxed{
\text{scale does not automatically correct structural training bias}
}
\]

The relevant question is not simply how much narrative text the model has seen.

It is:

\[
\boxed{
\text{What evidence-weighting structure was statistically rewarded across that text?}
}
\]

This is a hypothesis, not an established result. It requires controlled training experiments.

---

## 17. Where Weight Priors May Enter the Training Pipeline

TINWP should not be attributed exclusively to pretraining without evidence.

The operative weighting behaviour of a deployed system may emerge from several stages:

\[
W_{\text{model}}
=
f(
W_{\text{pretraining}},
W_{\text{instruction}},
W_{\text{preference}},
W_{\text{safety}},
W_{\text{deployment}}
).
\]

### Pretraining

Pretraining may establish broad statistical priors over which linguistic and narrative structures are most predictive.

### Instruction tuning

Instruction tuning may reward particular explanatory forms, such as explicit verbal justification, clear propositions, and directly stated motives.

### Preference optimization

If human raters prefer answers that are cautious, explicit, easily justified, socially conventional, or resistant to inferential leaps, preference optimization may indirectly favour direct linguistic evidence over distributed behavioural evidence.

### Safety tuning

Safety systems may appropriately discourage strong claims about motive, attraction, intent, risk, or mental state without direct evidence. If generalized too broadly, such caution could become an epistemically inappropriate weighting tendency in ordinary narrative interpretation.

### Deployment context

System prompts, memory systems, product policies, retrieval systems, and conversational history may further alter the effective weighting function.

The appropriate hypothesis is therefore:

> Systematic evidence-weight distortions observed at inference time may partly originate in learned priors produced by the statistical and optimization structure of training and post-training.

This is deliberately weaker than claiming that pretraining alone causes NEWD.

---

## 18. Can Inference-Time Reasoning Override Weight Priors?

A major competing explanation is that evidence-weight distortion may not reflect a deeply fixed prior.

A model may possess the relevant interpretive capability but fail to deploy it under ordinary inference conditions.

Additional reasoning, structured prompting, or explicit decomposition may allow the system to reweight evidence correctly.

This creates an important distinction:

\[
\text{weighting capability}
\]

versus:

\[
\text{default weighting behaviour}.
\]

A model may initially produce:

\[
\hat W_{\text{default}}
\]

but, when instructed to compare evidence classes, examine baseline changes, account for narrator asymmetry, or incorporate culture, produce:

\[
\hat W_{\text{reasoned}}
\approx
W^*.
\]

If so, the problem is not lack of capacity.

It is:

\[
\boxed{
\text{failure to spontaneously activate the appropriate weighting process}
}
\]

CAPRI is relevant here because sequential prompting improved cultural application even when cultural information was already inferable.

Prompt correction therefore does not by itself falsify TINWP. It may instead show:

\[
\text{default prior}
\rightarrow
\text{initial interpretation}
\]

followed by:

\[
\text{corrective scaffold}
\rightarrow
\text{reweighted interpretation}.
\]

A reliable system should not depend upon the user already knowing which interpretive variable the system failed to weight correctly.

---

## 19. Proposed Experiments

NEWD and TINWP are intended to be falsifiable.

### 19.1 Evidence-class substitution

Construct matched narratives supporting the same latent hypothesis through different evidence channels:

- explicit statement;
- repeated behaviour;
- baseline change;
- source-asymmetric narration;
- cross-event pattern;
- culturally constrained indirect behaviour.

Ask models to estimate the plausibility of the same hypothesis under each condition.

### 19.2 Pattern accumulation

Present individually ambiguous events sequentially.

Measure whether the model appropriately changes its overall inference as directional evidence accumulates, or whether it repeatedly resets to "each event could mean something else."

### 19.3 Baseline manipulation

Hold current behaviour constant while changing historical baseline.

If a model treats behaviour similarly despite major baseline differences, baseline evidence may be underweighted.

### 19.4 Source-asymmetry test

Provide explicit access to one actor's internal state but behavioural evidence for another actor whose latent state is experimentally matched.

Measure whether the narratively accessible actor is systematically assigned stronger underlying emotion or intent.

### 19.5 Cultural-weight test

Use identical surface behaviour under settings in which direct expression has different social costs.

The key measurement is not whether the model can describe the cultural difference, but whether its interpretation changes appropriately because of it.

### 19.6 Prompt-dependence test

Compare:

- culture merely inferable from context;
- culture explicitly stated;
- culture explicitly stated plus instruction to use it in interpreting behaviour.

Large differences between these conditions would suggest that relevant knowledge is available but not spontaneously operationalized.

### 19.7 Training-origin experiment

Construct synthetic training corpora containing identical underlying situations but systematically vary how evidence is represented.

**Corpus A — explicit-state dominant:** intentions are usually stated directly.

**Corpus B — behaviour dominant:** the same intentions are expressed through repeated actions.

**Corpus C — balanced:** explicit and behavioural evidence have matched frequency and reliability.

Train otherwise comparable small language models on each corpus.

Then test them on identical unseen narratives in which explicit and behavioural evidence conflict.

If later evidence weighting differs systematically across training conditions, that would provide causal evidence that training distribution can induce evidence-class priors.

### 19.8 Reasoning-budget test

Evaluate identical narratives under different inference-time reasoning budgets.

If distortion disappears reliably with minimal additional reasoning, the case for a deeply persistent weighting prior weakens.

If additional reasoning reduces but does not eliminate distortion, reasoning may be compensating for rather than erasing a learned prior.

---

## 20. Provisional Metrics

A simple experimental formulation is:

\[
NEWD =
\sum_{c=1}^{k}
\alpha_c
\left|
\hat w_c-w_c^*
\right|,
\]

where \(\hat w_c\) is the model's inferred weight for evidence class \(c\), \(w_c^*\) is a benchmark reference weight, and \(\alpha_c\) reflects the importance of that class to the experimental scenario.

Reference weights could be estimated in two ways.

### Synthetic ground truth

Narratives can be generated from predefined causal structures in which the reliability of each evidence class is controlled by construction.

### Human comparative weighting

Independent human raters can estimate hypothesis strength across matched narratives.

For culturally dependent scenarios, within-culture and outside-culture raters should be analysed separately.

Human judgment is not treated as objective truth. It provides a comparative benchmark for whether models exhibit systematic departures from culturally situated human inference.

A second quantity could measure **reweighting susceptibility**:

\[
\Delta W
=
\hat W_{\text{scaffolded}}
-
\hat W_{\text{default}}.
\]

Large \(\Delta W\) would suggest that a model possesses relevant interpretive capability but has unreliable default weighting.

---

## 21. Core Hypotheses

**H1 — Explicitness overweighting.**  
LLMs will assign disproportionate inferential weight to explicit verbal evidence relative to behaviourally equivalent repeated evidence in at least some narrative classes.

**H2 — Observability-weight confusion.**  
When one actor's internal state is narratively accessible and another's is represented behaviourally, models will infer stronger states for the narratively accessible actor even when experimental ground truth is matched.

**H3 — Pattern underweighting.**  
Models will under-adjust when several individually ambiguous observations form a consistent cross-event pattern.

**H4 — Baseline underweighting.**  
Models will insufficiently alter interpretation when identical current behaviour represents a major departure from a long-established baseline.

**H5 — Cultural weight rigidity.**  
Models will insufficiently recalibrate the evidentiary significance of indirect behaviour when direct expression carries different cultural or social costs.

**H6 — Cultural knowledge/application gap.**  
Models may correctly identify the relevant cultural norm but fail to alter evidence weighting accordingly.

**H7 — Prompt-dependent cultural reweighting.**  
Explicit instructions to consider local culture will materially alter some interpretations even when the cultural information was already available.

**H8 — Training-Induced Narrative Weight Priors.**  
Systematic variation in how evidence classes are represented during training will produce persistent differences in later narrative evidence weighting.

**H9 — Inference-Time Reweighting.**  
Additional reasoning or explicit evidence decomposition will reduce some forms of NEWD, but the magnitude of correction will vary across model families and evidence classes.

---

## 22. Falsification and Discrimination

NEWD should be weakened or rejected if controlled testing finds that leading models:

1. assign stable, context-appropriate relative weights across evidence classes;
2. reliably distinguish narrative observability from underlying-state magnitude;
3. integrate repeated weak evidence appropriately;
4. adjust strongly and consistently to historical baseline information;
5. recalibrate behavioural evidence appropriately under cultural constraints;
6. apply cultural context equally well whether it is implicit, inferred, or explicitly foregrounded;
7. show no systematic difference between explicit and behavioural evidence once reliability is controlled.

TINWP specifically would be weakened if:

1. models trained on substantially different narrative distributions display essentially identical evidence-weight profiles;
2. synthetic training interventions fail to alter later evidence weighting;
3. distortions disappear reliably under minimal additional reasoning;
4. model weighting follows only immediate prompt structure with little persistent default tendency;
5. observed distortions are better explained by retrieval, sequence, context-window, or output-policy failures.

Evidence for TINWP would strengthen if controlled changes in training distribution produce predictable, persistent changes in weighting on unseen narratives.

A theory that cannot lose is not useful.

---

## 23. Agentic Safety Implications

In an ordinary chatbot, distorted weighting can produce a poor interpretation.

In an agentic system:

\[
E
\rightarrow
\hat W
\rightarrow
\hat I
\rightarrow
\hat S
\rightarrow
A.
\]

The evidence may all be present.

No fact needs to be hallucinated.

Nothing needs to be retrieved incorrectly.

No malicious objective is necessary.

The system can fail because:

\[
\boxed{
\text{it considered the right things in the wrong proportions}
}
\]

That matters in interpersonal advice, workplace disputes, medical-history interpretation, legal narratives, fraud investigation, intelligence analysis, personnel decisions, cross-cultural negotiation, compliance, and autonomous planning.

Culture adds a further risk. Globally deployed agents may encounter identical surface behaviours whose evidentiary meaning differs because:

\[
P(B|H,C_1)\neq P(B|H,C_2).
\]

If culture does not alter operative evidence weights, a system can appear culturally knowledgeable while systematically misreading people.

Increasing context length does not automatically solve this problem.

More evidence without reliable weighting can simply provide more material to weight incorrectly.

---

## 24. Possible Mitigations

A more reliable interpreter could separate evidence extraction from evidence synthesis.

### Stage 1 — Evidence inventory

Represent each item explicitly by content, source, type, time, reliability, and relationship to baseline.

### Stage 2 — Context inventory

Represent interpretively relevant constraints: culture, social norms, relationship structure, power, reputational cost, historical baseline, and source position.

### Stage 3 — Pattern construction

Identify recurrence, directional consistency, baseline change, contradictions, source asymmetries, cultural constraints, and action costs.

### Stage 4 — Explicit weighting

Require the system to state which evidence classes should matter more or less in the current setting and why.

### Stage 5 — Cultural counterfactual

Ask whether the behaviour would carry the same significance if direct expression carried little social cost.

### Stage 6 — Competing hypotheses

Evaluate several plausible hypotheses against the same evidence vector rather than constructing one interpretation and defending it.

### Stage 7 — Reopening rule

When a user supplies a missing contextual variable that should materially change evidence weights, the system should reopen the interpretation rather than merely append the new fact to the old conclusion.

The architectural principle is:

\[
\boxed{
\text{evidence retrieval}
\neq
\text{evidence weighting}
}
\]

and:

\[
\boxed{
\text{cultural retrieval}
\neq
\text{culture-conditioned reasoning}
}
\]

---

## 25. Conclusion

Narrative interpretation is not merely a retrieval problem.

It is not merely a sequencing problem.

It is not merely an evidentiary-threshold problem.

It is not solved merely by adding cultural knowledge.

It is also a **weighting problem**.

A model can correctly retain the evidence, preserve its sequence, maintain its epistemic roles, and recognize relevant cultural information while still reaching the wrong interpretation because its relative evidence weights are inappropriate.

The central NEWD proposition is therefore:

\[
\boxed{
\text{correct evidence}
+
\text{correct sequence}
+
\text{correct epistemic roles}
+
\text{wrong weights}
=
\text{wrong interpretation}
}
\]

The cultural extension is:

\[
\boxed{
\text{a model has not operationally understood culture merely because it can describe it}
}
\]

and the training-origin question is:

\[
\boxed{
\text{Did the model merely interpret the narrative badly, or was it trained to weight narratives badly?}
}
\]

The broader proposition is simple:

\[
\boxed{
\text{understanding a narrative requires knowing not only what happened, but how much each thing should matter}
}
\]

---

## References

Brei, A., Henry, K., Sharma, A., Srivastava, S., & Chaturvedi, S. (2025). **Classifying Unreliable Narrators with Large Language Models.** *Proceedings of the 63rd Annual Meeting of the Association for Computational Linguistics*, 20766–20791. https://doi.org/10.18653/v1/2025.acl-long.1013

Jung, D., Choi, J., Chae, S., & Jung, S. (2026). **Style over Story: Measuring LLM Narrative Preferences via Structured Selection.** *Findings of the Association for Computational Linguistics: ACL 2026*, 27304–27331. https://doi.org/10.18653/v1/2026.findings-acl.1361

Kouwenhoven, T., van der Meer, M. T., & van Duijn, M. J. (2026). **Traces of Social Competence in Large Language Models.** *Proceedings of the 30th Conference on Computational Natural Language Learning*, 742–759. https://doi.org/10.18653/v1/2026.conll-main.45

Miao, Y., Zhu, J., & Shwartz, V. (2026). **LLMs Infer Cultural Context but Fail to Apply It When Responding.** arXiv:2606.17688. https://arxiv.org/abs/2606.17688

Rao, A., Yerukola, A., Shah, V., Reinecke, K., & Sap, M. (2025). **NormAd: A Framework for Measuring the Cultural Adaptability of Large Language Models.** *Proceedings of NAACL 2025*, 2373–2403. https://doi.org/10.18653/v1/2025.naacl-long.120

Zhao, J., Fang, M., Zhang, K., & Pechenizkiy, M. (2025). **Unmasking Style Sensitivity: A Causal Analysis of Bias Evaluation Instability in Large Language Models.** *Proceedings of ACL 2025*, 16314–16338. https://doi.org/10.18653/v1/2025.acl-long.796

---

*Working paper. The component problems discussed here—narrative preference, unreliable narration, style sensitivity, cultural-adaptation failure, and training-emergent linguistic effects—are not claimed as novel. The proposed contribution is the narrower failure mechanism of context-sensitive relative evidentiary weighting, together with the NEWD and TINWP hypotheses and their experimental discrimination from retrieval, sequence, threshold, cultural-knowledge, and inference-time failures.*