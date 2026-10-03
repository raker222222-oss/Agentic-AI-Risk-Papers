# Visibility Within an Information System Is Not Agency in the Real World
## A Pilot Study of Channel-to-Total Generalization in Large Language Models

**Rakesh Rajan (Rakesh OSS)**  
**Working paper**

## Abstract

Human relationships and organizational activity are distributed across multiple communication and action channels. Prior work on **media multiplexity** shows that important social ties commonly span text, telephone, face-to-face interaction, and other media rather than residing within a single channel. Research on multiplex-network sampling has separately shown that observing selected communication layers can generate misleading properties in the observed sample, while multimodal-learning research treats modality availability as potentially **missing not at random**. Recent studies also show that large language models can infer social relationships and romantic attraction from conversational evidence.

The present pilot isolates a different question: **when one actor is more visible than another within an observed information channel, do large language models generalize that visibility into a judgment about the actors' overall agency in the underlying real-world system?**

Claude, Gemini, and Perplexity were evaluated across two domains: interpersonal relationship development and workplace project execution. In each domain, systems first received a record in which one actor was substantially more visible within the observed communication channel. They were then tested under three additional conditions: restoration of consequential off-channel behavior, reassignment of the visible behavior to the opposite actor, and an explicit warning that important activity might be absent from the observed channel.

Across all six model-domain combinations, the actor dominant in the visible channel was initially judged to have greater overall agency. When consequential off-channel behavior was restored, none of the six evaluations retained that judgment: three shifted to roughly equal agency and three reversed to the previously less-visible actor. Reassigning the visible interaction pattern to the opposite actor produced a corresponding reversal in all six cases. Explicit observation-boundary warnings produced epistemic restraint in only three of six conditions.

The pilot proposes **Channel-to-Total Generalization Error (CTGE)**: the extension of actor-specific visibility within a partial information system into a judgment about agency in the larger system that the channel only incompletely represents.

---

## 1. The Problem

AI systems increasingly evaluate people from digital traces: messaging histories, Slack or Teams records, CRM logs, support tickets, family group chats, and other machine-visible records.

An unstated assumption can enter such evaluations:

$$
\text{observed activity} \approx \text{total relevant activity}.
$$

But communication research gives strong reasons not to assume this equivalence. Media-multiplexity research treats interpersonal communication as occurring across an ecosystem of channels rather than through one isolated medium. Strong ties commonly use combinations of text, telephone, social media, and face-to-face interaction.

Therefore:

$$
\boxed{\text{channel completeness} \neq \text{system completeness}}
$$

A complete Slack archive is not necessarily a complete record of project contribution.

A complete WhatsApp export is not necessarily a complete record of a relationship.

The central question is:

> **Do large language models preserve the distinction between agency visible in one information channel and agency in the larger real-world interaction?**

---

## 2. Related Work and Distinction

### 2.1 Media Multiplexity

Media-multiplexity research has long argued that social ties often span multiple channels. Jamieson, Boase, and Kobayashi show that communication frequency, cognitive closeness, and social role are associated with greater use of multiple media. Related work treats close relationships as a **media ecosystem** rather than a single-channel process.

This establishes:

$$
\text{one communication channel} \neq \text{the entire social interaction}.
$$

It does not, however, directly test whether an LLM attributes greater **overall interpersonal agency** to whichever participant happens to be more visible in the sampled channel.

### 2.2 Single-Channel Sampling Bias

Network-science research provides a closely related methodological warning. Murase et al. model cases in which people choose among communication channels while researchers observe only a restricted subset. Behavior-dependent sampling of a multiplex network can create apparent properties absent from the underlying network, making naive generalization from the sample unsafe.

Prior work here concerns network properties such as degree distributions, clustering, or correlations. The present study instead asks a person-level question:

$$
\text{Who is driving the underlying interaction?}
$$

### 2.3 Missing and Non-Random Modalities

Incomplete multimodal information is already an established machine-learning problem. Liang, Pan, and Xiong study multimodal clinical records in which modality availability is not random but can depend on underlying decision processes.

The present study treats such missingness as a **data-generation condition**, not as the final failure. The target mechanism is:

$$
\text{actor-correlated visibility}
\rightarrow
\text{overall relative-agency judgment}.
$$

### 2.4 LLM Social and Relationship Inference

Recent work demonstrates that LLMs make judgments about interpersonal relationships from conversational evidence. Matz et al. show that models can detect some verbal indicators of romantic attraction, while noting that relevant non-verbal information may be unavailable to text-based systems. Guan et al. examine speaker-relationship inference across modality settings. Hou, Leach, and Huang evaluate ChatGPT relationship advice and find disagreement and inconsistency.

These studies establish that:

$$
\text{LLMs make social judgments from conversational evidence}.
$$

They do not directly isolate the controlled actor-visibility crossover tested here.

### 2.5 Specific Contribution

The adjacent literatures establish important pieces of the problem:

- relationships and work are multi-channel;
- single-channel samples can be systematically biased;
- modalities can be missing non-randomly;
- LLMs infer social states from conversational evidence.

The narrower question tested here is:

> **If two actors distribute consequential activity differently across observable and unobservable channels, will an LLM mistake differential visibility for differential overall agency?**

The distinction is:

$$
\boxed{\text{Prior work: incomplete or multiplex observation}}
$$

versus:

$$
\boxed{\text{Present work: person-level agency generalization from actor-correlated visibility}}.
$$

---

## 3. Proposed Failure Mechanism

### 3.1 Actor-Correlated Modality Missingness

Let the complete behavior of actors (A) and (B) be:

$$
D_A=D_A^{visible}+D_A^{hidden}
$$

$$
D_B=D_B^{visible}+D_B^{hidden}.
$$

If the probability of consequential activity being visible differs systematically between actors,

$$
P(V\mid A)\neq P(V\mid B),
$$

then the observation process itself is actor-correlated.

This paper calls that condition **Actor-Correlated Modality Missingness (ACMM)**.

The problem is not merely that information is missing. The missingness is distributed differently across actors.

### 3.2 Channel-to-Total Generalization Error

Let (G_A^c) represent agency visible for actor (A) in channel (c), while (G_A^*) represents total agency across the underlying interaction.

A Channel-to-Total Generalization Error occurs when a model implicitly treats:

$$
G_A^c>G_B^c
$$

as sufficient evidence for:

$$
G_A^*>G_B^*.
$$

The error is not that the model identifies who is more active in the visible channel. The error occurs when the conclusion is extended beyond the evidentiary boundary of the channel.

### 3.3 Visibility-Induced Agency Reversal

A diagnostic crossover occurs when the actor associated with the dominant visible behavior is changed while the structure of the observed record remains otherwise equivalent:

$$
A_{visible}\rightarrow A_{judged\ more\ agentic}
$$

and

$$
B_{visible}\rightarrow B_{judged\ more\ agentic}.
$$

This serves primarily as a manipulation check rather than as proof of error by itself.

---

## 4. Experimental Design

Three external AI systems were tested:

- Claude;
- Gemini;
- Perplexity.

Two domains were used:

1. interpersonal relationship development;
2. workplace project execution.

Each domain contained four conditions.

### Condition A — Visible-Channel Record

One actor displayed substantially more observable initiative in the supplied communication channel. The model was asked which actor had greater **overall** agency.

### Condition B — Full Chronology

The visible record was supplemented with consequential actions by the initially less-visible actor occurring through calls, meetings, visits, technical work, or other channels.

### Condition C — Visibility Crossover

The visible-channel behavior was reassigned to the opposite actor. This tested whether the overall agency judgment followed actor identity or observable activity.

### Condition D — Observation-Boundary Warning

The original visible-channel record was retained, but the model was explicitly informed that substantial calls, meetings, visits, technical actions, or other activity might be absent. The question continued to ask about **overall** agency.

Models were required to choose:

- A — Actor A has greater overall agency;
- B — Actor B has greater overall agency;
- E — roughly equal;
- I — insufficient evidence.

Confidence was also requested.

---

## 5. Results: Relationship Domain

| Model | Visible channel | Full chronology | Visibility crossover | Boundary warning |
|---|---|---|---|---|
| Claude | A, 88% | E, 60% | B, 88% | I, 60% |
| Gemini | A, 85% | E, 95% | B, 95% | I, 95% |
| Perplexity | A, 92% | B, 78% | B, 95% | A, 88% |

All three systems initially judged the more text-visible actor as having greater overall relationship agency.

When consequential off-channel behavior was restored:

- Claude shifted from A to equal;
- Gemini shifted from A to equal;
- Perplexity reversed from A to B.

No system retained the original A judgment.

---

## 6. Results: Workplace Domain

| Model | Slack-visible record | Full chronology | Visibility crossover | Boundary warning |
|---|---|---|---|---|
| Claude | A, 90% | B, 78% | B, 93% | I, 55% |
| Gemini | A, 100% | E, 95% | B, 100% | A, 85% |
| Perplexity | A, 95% | B, 82% | B, 96% | A, 94% |

The workplace experiment reproduced the central pattern.

In the visible-channel condition, Employee A dominated Slack through priorities, assignments, reminders, timelines, meeting coordination, progress checks, and risk summaries. All three systems judged A to have greater overall project agency.

The full chronology then introduced Employee B's less-visible but consequential actions: identifying a client-data mismatch, obtaining corrected specifications, working with engineering to fix transformation logic, resolving a disputed customer requirement, detecting and correcting a production configuration problem, helping another teammate solve a technical blocker, securing client agreement on a revised approach, and confirming readiness for the next stage.

After these actions were restored:

- Claude reversed from A to B;
- Gemini shifted from A to equal;
- Perplexity reversed from A to B.

Again, zero of three systems retained the original A judgment.

---

## 7. Aggregate Pilot Result

Across both domains there were six model-domain evaluations.

In Condition A:

$$
\boxed{6/6}
$$

judged the actor most visible in the observed channel to have greater overall agency.

In Condition B:

$$
\boxed{0/6}
$$

retained that judgment after consequential off-channel behavior was restored.

Specifically:

$$
3/6:\ A\rightarrow E
$$

and:

$$
3/6:\ A\rightarrow B.
$$

In Condition C:

$$
\boxed{6/6}
$$

assigned greater agency to the actor receiving the dominant visible-channel pattern.

Thus:

$$
A_{visible}\rightarrow A
$$

and:

$$
B_{visible}\rightarrow B
$$

in every tested model-domain combination.

---

## 8. Observation-Boundary Warning

Condition D produced a second finding.

The systems were explicitly warned that the supplied channel might omit consequential activity.

Results:

$$
3/6\rightarrow I
$$

and:

$$
3/6\rightarrow A.
$$

Claude responded with epistemic restraint in both domains. Gemini responded with restraint in the relationship domain but not the workplace domain. Perplexity retained the visible-actor judgment in both domains.

This suggests:

$$
\boxed{
\text{recognition of missing evidence}
\neq
\text{operative adjustment for missing evidence}
}
$$

A model may correctly state that consequential evidence could be absent while nevertheless making nearly the same high-confidence overall judgment.

Perplexity provided the clearest examples. In the workplace condition:

$$
A_{visible}=95\%
$$

and after the observation warning:

$$
A_{warning}=94\%.
$$

Yet when the previously missing actions were actually supplied:

$$
B_{full}=82\%.
$$

Thus:

$$
\text{partial record}\rightarrow A
$$

$$
\text{partial record + explicit uncertainty}\rightarrow A
$$

but:

$$
\text{actual missing evidence}\rightarrow B.
$$

This may represent a related phenomenon of **epistemic caveat–conclusion decoupling**: a valid uncertainty condition is stated but does not propagate sufficiently into the operative judgment or confidence.

---

## 9. Interpretation

The experiment does not show that systems should ignore observed communication.

If one actor sends more messages, coordinates more Slack activity, or initiates more visible actions, concluding that this actor has greater **channel-specific agency** is reasonable.

The problem arises when:

$$
\text{agency in observed system}
$$

is converted into:

$$
\text{agency in underlying real-world system}.
$$

The appropriate distinction is:

$$
\boxed{
\text{visible-system agency}
\neq
\text{total-system agency}
}.
$$

The pilot suggests that current systems may fail to preserve this boundary reliably.

---

## 10. Why the Workplace Result Matters

The relationship domain could potentially be dismissed as inherently ambiguous.

The workplace replication substantially reduces that objection. The relevant off-channel actions were concrete: technical defects were identified, client disagreements were resolved, configurations were corrected, failing tests became successful, and blockers were removed.

Yet when those actions were absent from the communication record, all three systems attributed greater overall project agency to the person generating more visible coordination activity.

The general problem therefore extends beyond social interpretation. It can occur whenever:

$$
\boxed{
\text{digital-trace visibility is unevenly distributed across contributors}
}.
$$

---

## 11. Potential Real-World Applications

The mechanism could matter wherever AI evaluates people from partial information systems.

### Workplace Evaluation

$$
\text{Slack activity}\not\equiv\text{work contribution}
$$

### Sales Analysis

$$
\text{CRM activity}\not\equiv\text{sales agency}
$$

### Customer Service

$$
\text{ticket visibility}\not\equiv\text{customer experience}
$$

### Caregiving

$$
\text{family-chat activity}\not\equiv\text{caregiving contribution}
$$

### Relationships

$$
\text{text messaging}\not\equiv\text{relationship agency}
$$

### Organizational Analytics

$$
\text{machine-visible work}\not\equiv\text{valuable work}.
$$

---

## 12. Limitations

This is a pilot study. The scenarios were deliberately constructed to test whether the proposed mechanism can occur.

The results do **not** establish:

- population prevalence;
- frequency in deployed systems;
- universality across LLM families;
- magnitude under naturally occurring data;
- that every single-channel inference is unreliable.

The present experiment establishes something narrower:

> A channel-to-total agency generalization can be produced reproducibly across multiple widely used AI systems and across more than one domain.

The model sample and scenario sample are small. The evaluations were conducted manually through separate fresh chats rather than through an automated API benchmark, and exact system versions were not independently fixed by the study. Confidence values are model self-reports rather than calibrated probabilities.

The present literature search also cannot establish absolute novelty. It establishes only that we did not locate prior work directly testing the same controlled actor-visibility crossover and overall-agency inference mechanism.

Further experiments should preregister a larger benchmark covering multiple domains, visibility ratios, degrees of missingness, event importance levels, actor identities, ordering variations, and model families.

---

## 13. Falsification Criteria

The hypothesis would be weakened if, under larger preregistered tests:

1. models consistently distinguish channel-specific from total-system agency without prompting;
2. crossover manipulations cease to affect overall-agency judgments;
3. restoring off-channel activity rarely changes the original judgment;
4. observed effects disappear after controlling for event importance and message frequency;
5. human evaluators exhibit identical behavior at comparable rates;
6. observation-boundary warnings reliably prevent unsupported generalization across models and domains.

---

## 14. Conclusion

A complete record of an information channel is not necessarily a complete record of the system it represents.

Prior research already establishes that human communication is multiplex, that observing selected communication layers can induce sampling bias, that modalities can be missing non-randomly, and that LLMs can make social judgments from conversational evidence.

The present pilot isolates a narrower candidate failure mechanism.

Claude, Gemini, and Perplexity repeatedly attributed greater **overall agency** to the actor whose behavior was most visible within the supplied information channel.

When consequential off-channel actions were restored, none of the six model-domain evaluations retained its original judgment.

The central distinction is:

$$
\boxed{
\text{everything visible}
\neq
\text{everything that happened}
}.
$$

More generally:

$$
\boxed{
\textbf{visibility within an information system is not equivalent to agency within the underlying real-world system.}
}
$$

For AI systems increasingly asked to evaluate workers, customers, relationships, organizations, and human behavior from digital traces, failure to preserve this distinction could produce systematic errors precisely where the available record appears most complete.

---

## References

Guan, Y., Lu, Y.-J., Wang, Y., Lee, J., Villalba, J., Moro Velazquez, L., Thebaud, T., & Dehak, N. (2026). *Who Are They to Each Other? Multi-Agent Reasoning for Speaker Relationship Inference*. arXiv:2609.09628. https://arxiv.org/abs/2609.09628

Hou, H., Leach, K., & Huang, Y. (2024). ChatGPT Giving Relationship Advice — How Reliable Is It? *Proceedings of the International AAAI Conference on Web and Social Media, 18*(1), 610–623. https://ojs.aaai.org/index.php/ICWSM/article/view/31338

Jamieson, J., Boase, J., & Kobayashi, T. (2018). Multiplying the Medium: Tie Strength, Social Role, and Mobile Media Multiplexity. In *The Oxford Handbook of Networked Communication*, 243–259. https://academic.oup.com/edited-volume/34286/chapter-abstract/290656697

Liang, Z., Pan, Z., & Xiong, R. (2025). Causal Representation Learning from Multimodal Clinical Records under Non-Random Modality Missingness. *Proceedings of EMNLP 2025*, 28791–28808. https://aclanthology.org/2025.emnlp-main.1465/

Matz, S. C., Peters, H., Cerf, M., Grunenberg, E., Eastwick, P. W., Back, M., Finkel, E. J., et al. (2026). Large language models can detect verbal indicators of romantic attraction. *Scientific Reports, 16*, 21441. https://www.nature.com/articles/s41598-026-52308-x

Murase, Y., Jo, H.-H., Török, J., Kertész, J., & Kaski, K. (2019). Sampling networks by nodal attributes. *Physical Review E, 99*, 052304. https://journals.aps.org/pre/abstract/10.1103/PhysRevE.99.052304

Taylor, S. H., & Bazarova, N. N. (2021). Always Available, Always Attached: A Relational Perspective on the Effects of Mobile Phones and Social Media on Subjective Well-Being. *Journal of Computer-Mediated Communication, 26*(4), 187–206. https://academic.oup.com/jcmc/article/26/4/187/6357206
