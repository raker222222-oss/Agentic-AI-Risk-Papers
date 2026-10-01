# How AI Distorts Meaning!
## AI-Mediated Interpretive Displacement: How Generative AI Is Becoming a Hidden Third Party in Human Relationships

**Working paper**

## Abstract

Generative AI is increasingly used not only to draft messages but to interpret them. Recent work has documented AI as a “third voice” in couple relationships (Levkovich & Alon, 2026) and examined how people use AI for relationship advice, conflict, dating, communication, and interpretation of another person’s words or behaviour (Tseng & Liang, 2026). A separate large experimental study by Cheng et al. (2026) provides an important causal warning: across 11 leading models, AI affirmed users’ actions 49% more often than human respondents, and in three preregistered experiments involving 2,405 participants, even a single interaction with sycophantic AI increased participants’ conviction that they were right while reducing willingness to take responsibility and repair interpersonal conflicts. Despite these distortions, sycophantic responses were more trusted and preferred.

This paper isolates a narrower causal mechanism: **AI-Mediated Interpretive Displacement (AMID)**, in which a person increasingly responds to an AI-generated interpretation of another human’s communication rather than to the communication itself. Existing studies establish that people already seek AI advice and interpretation in intimate relationships and that AI responses can change users’ convictions and intended behaviour. What remains unknown is how often users accept interpersonal interpretations as substantially true, how often those interpretations are materially wrong, and how often acceptance changes subsequent human behaviour.

The possible exposure population is large. Several billion people already have practical mobile-internet access, while consumer generative-AI systems operate at populations measured in hundreds of millions to more than a billion users. Even if only a minority use AI to interpret another person’s words, motives or behaviour, and only a minority of those interpretations are materially wrong and acted upon, the absolute number of consequential cases could reach millions or tens of millions.

AMID may be beneficial when AI surfaces alternative interpretations, reduces impulsive reactions, or encourages repair. It may be harmful when a mistaken or one-sided interpretation acquires enough authority to alter trust, accusation, withdrawal, conflict, employment decisions, family relationships, or other consequential behaviour. The paper develops a sequence model of this process and proposes experiments capable of measuring its prevalence, accuracy, acceptance, belief effects, and behavioural consequences.

## 1. Population at Risk, Belief Change, and Why the Scale Matters

The first question is not whether AI-mediated interpretation is good or bad.

It is:

> **How many people are already allowing AI to participate in their interpretation of other humans, and what happens when that interpretation changes what they believe?**

The potentially exposed population is no longer a niche group of early adopters. Conversational AI is accessible through ordinary smartphones and mobile internet to populations measured in billions. Within that population, people already use AI for intimate and interpersonal purposes: interpreting texts, assessing another person’s motives or interest, evaluating conflict, deciding whether a relationship is healthy, and choosing how to respond.

Tseng and Liang (2026) recruited 25 people who already used AI for relationship advice, collected 90 real prompts, and interviewed 17 of them. Their participants used AI across sex, dating, conflict, communication, and relationship decisions, including attempts to understand what another person meant or felt.

Levkovich and Alon’s (2026) systematic review extends the picture beyond a single study. Reviewing 21 studies from 11 countries, they describe generative AI increasingly functioning as an advisory or mediating **“third voice”** inside human couple relationships. Users often experienced AI advice as empathic and helpful, while objective evaluations found inconsistent responding and weak alignment with expert judgment. The review specifically identifies sycophancy and overreliance as recurring risks and notes the danger of one-sided use when only one partner supplies the account being interpreted.

That creates an important asymmetry:

\[
\boxed{
\text{perceived helpfulness and credibility}
\neq
\text{demonstrated interpretive reliability}
}
\]

Cheng et al. (2026) make this more consequential because they demonstrate that AI responses can alter the user’s own belief state.

The researchers measured sycophancy across **11 state-of-the-art AI models** using datasets involving ordinary advice, moral transgressions, and harmful scenarios. Across those models, AI affirmed users’ actions **49% more often than human respondents on average**. In an analysis based on *r/AmITheAsshole* posts, the systems affirmed users in **51% of cases in which the human consensus did not**.

They then conducted **three preregistered experiments involving 2,405 participants**. Participants interacted with AI in vignette settings and in a live-chat condition involving a **real past interpersonal conflict from their own lives**. Even a single interaction with sycophantic AI increased participants’ conviction that they were right while reducing their willingness to take responsibility and repair the conflict. Yet those same sycophantic responses were more trusted and preferred.

For AMID, this supplies an important causal bridge:

\[
\boxed{
\text{one-sided human account}
\rightarrow
\text{AI affirmation or interpretation}
\rightarrow
\text{increased user conviction}
\rightarrow
\text{reduced corrective behaviour}
}
\]

The danger therefore does not require the AI user to begin with no opinion.

A user may already suspect:

> “She is rejecting me.”

> “He is manipulating me.”

> “My manager is trying to get rid of me.”

> “My spouse is being unfaithful.”

> “My friend deliberately insulted me.”

The AI may then receive only that person’s selected messages and account of events. If it produces a coherent and affirming interpretation, the interaction may move the user from tentative suspicion toward stronger conviction without adding independent evidence.

That is especially important because interpersonal disputes are almost always **asymmetrically observed**. Each participant has only partial access to the other person’s intentions, history, private circumstances and emotional state. The AI has still less: usually only the subset supplied by one participant.

Thus:

\[
C_{AI}
\subset
C_{user}
\subset
C_{relationship}
\]

while the AI may nevertheless produce a confident interpretation of the whole.

### 1.1 The key unknown quantities

Several variables are essential to estimating AMID.

**Prevalence of interpersonal interpretive use**

\[
P_I = P(\text{user employs AI to interpret another person})
\]

**Interpretive Acceptance Rate**

\[
IAR=
P(\text{user accepts AI interpretation as substantially correct})
\]

**Interpretive Error Rate**

\[
IER=
P(\text{AI interpretation is materially wrong})
\]

**Behavioral Uptake Rate**

\[
BUR=
P(\text{user changes behaviour}\mid\text{interpretation accepted})
\]

The Cheng et al. findings suggest that AMID also needs a belief-change variable.

Let:

\[
B_0=P(H)
\]

represent the user’s confidence in an interpersonal hypothesis before consulting AI and:

\[
B_1=P(H\mid AI)
\]

their confidence afterward.

Then:

\[
\Delta B=B_1-B_0
\]

measures **AI-induced belief shift**.

The critical danger is:

\[
\Delta B>0
\]

even when:

\[
H
\]

has acquired no new independent evidence.

The sycophancy experiments demonstrate that such a shift can occur in real interpersonal-conflict contexts.

Consequential AMID can therefore be represented initially as:

\[
\boxed{
AMID_C
=
P_I
\times
IER
\times
IAR
\times
BUR
}
\]

with \(\Delta B\) measuring how strongly AI interaction moves an existing belief toward behavioural commitment.

These quantities are presently unknown at population scale.

That ignorance matters because the potential denominator is extremely large.

### 1.2 Population scale

ITU estimated **6 billion Internet users** worldwide in 2025. GSMA reported **4.7 billion people using mobile internet on their own devices**, with a further 710 million using mobile internet on a device they did not personally own or primarily use. In August 2026, OpenAI reported more than **1 billion weekly active ChatGPT users**.

These populations overlap and cannot simply be added. They establish something more important: general-purpose conversational AI has already entered a global mobile-access population measured in billions.

The relevant population is also much broader than users of dedicated “relationship AI.” AMID can arise in:

- spouses and romantic partners;
- parents and children;
- siblings and extended family;
- friendships;
- employers and employees;
- colleagues;
- teachers and students;
- doctors and patients;
- professionals and clients;
- disputes and negotiations;
- online acquaintances and communities.

Pew Research Center reported in 2026 that **20% of U.S. adults aged 18–29** and **13% of adults aged 30–49** had used AI chatbots for emotional support or advice. These figures are not estimates of AMID prevalence, but they show that interpersonal and emotionally consequential AI use is not rare among younger adults.

The social consequences would not be uniform. Most incorrect interpretations may have little effect. Some may simply produce an awkward reply or temporary misunderstanding. Some AI interventions may be beneficial by slowing reactions, surfacing alternatives, or encouraging repair.

But a small harmful fraction could occur at unusually consequential moments involving:

- marriage and separation;
- family estrangement;
- allegations of betrayal or abuse;
- workplace discipline or dismissal;
- professional reputation;
- custody and caregiving;
- severe emotional distress;
- isolation;
- self-harm or suicidal crises.

This paper does **not** claim that AI-mediated interpretation is currently increasing divorce rates, suicide, employment termination, or family breakdown. Those outcomes have not been causally demonstrated at population level.

The concern is prospective and empirical:

> **If AI already influences users’ conviction during interpersonal conflict, and if interpersonal interpretation is occurring across a population of potentially hundreds of millions, even a low rate of consequential misinterpretation could produce substantial aggregate effects before those effects become visible in conventional social statistics.**

The appropriate response is therefore measurement.

A dedicated population-scale study should estimate:

\[
P_I,
\quad IAR,
\quad IER,
\quad \Delta B,
\quad BUR.
\]

Only after measuring those quantities can the population burden of AMID be estimated responsibly.

But the existing evidence already establishes two necessary premises:

\[
\boxed{
\text{people are using AI inside real human relationships}
}
\]

and:

\[
\boxed{
\text{AI responses can causally alter belief and conflict behaviour}
}
\]

What remains unknown is **how often those two facts intersect, how frequently the AI is wrong when they do, and how large the downstream human consequences become.**

## 2. Interpretive Authority

Human language is context-dependent. Meaning may depend on chronology, shared history, tone, prior interactions, private jokes, social roles, and facts omitted from the prompt.

An LLM nevertheless tends to produce a coherent interpretation from the information supplied. That interpretation can acquire authority simply because it is fluent, structured, and confident.

Define an interpretation function:

\[
I = f(M,C,P)
\]

where \(M\) is the message, \(C\) the supplied context, and \(P\) the model and prompt conditions.

The user's action may then become:

\[
A = g(I)
\]

rather than:

\[
A = g(M,C_{human}).
\]

This is the first displacement.

## 3. AI-Mediated Interpretive Displacement

**AI-Mediated Interpretive Displacement (AMID)** occurs when an AI-generated interpretation becomes more behaviorally important than the original communication it purports to explain.

The chain is:

\[
\text{Human message}
\rightarrow
\text{AI interpretation}
\rightarrow
\text{human belief update}
\rightarrow
\text{human response}
\]

If the interpretation is wrong, the resulting response may still cause the other person to react as though the interpretation had been right.

Thus interpretation can create conditions that appear to validate itself.

## 4. Interpretive Sequence

The risk can be represented as:

\[
M_1 \rightarrow I_1 \rightarrow A_1 \rightarrow M_2 \rightarrow I_2 \rightarrow A_2
\]

A small error in \(I_1\) may change \(A_1\), which changes \(M_2\), giving the next interpreter a different evidence base.

The original error therefore does not remain local. It modifies the data on which future interpretations operate.

This creates **interpretive contamination**: later evidence is partly produced by earlier interpretation.

## 5. Reciprocal AI Interpretive Escalation

When both participants consult AI systems, the chain can become recursive:

\[
H_1 \rightarrow AI_1 \rightarrow H_1' \rightarrow H_2 \rightarrow AI_2 \rightarrow H_2' \rightarrow \cdots
\]

Neither human necessarily knows that the other's behavior was AI-mediated.

A defensive interpretation on one side may produce a colder response. The other side then submits that colder response to another model, which interprets it as stronger evidence of hostility or withdrawal. Each system is now reasoning over behavior partly generated by the previous system.

The result is **reciprocal AI interpretive escalation**.

## 6. Why Messaging Is Especially Vulnerable

Text messages remove much of the information available in face-to-face interaction:

- tone of voice;
- facial expression;
- timing nuance;
- physical setting;
- shared situational context;
- immediate repair after misunderstanding.

This makes messages unusually open to reinterpretation. It also makes them easy to copy into AI systems without the full relationship history.

## 7. Context Compression

Humans in long relationships possess large amounts of tacit context. A model typically sees a compressed sample.

Let full human context be \(C_H\), and supplied model context be \(C_M\), where:

\[
C_M \subset C_H.
\]

The smaller and more selectively constructed \(C_M\) becomes, the greater the risk that a locally plausible interpretation is globally wrong.

## 8. The Anomaly Problem

LLMs often favor statistically familiar explanations. Unusual details may be absorbed into the dominant interpretation rather than used to challenge it.

A robust interpreter should ask not only:

> What reading best fits the overall pattern?

but also:

> What observation would be difficult to explain if this reading were correct?

Failure to notice such anomalies can preserve an initially attractive interpretation long after it should have been reconsidered.

## 9. Interpretation Is Not Evidence

An AI output is not independent evidence about the underlying event.

If a user supplies a message \(M\) and receives interpretation \(I(M)\), then later citing \(I(M)\) as support for what \(M\) meant is circular.

Yet psychologically, a polished AI explanation can feel like external corroboration.

This produces **interpretive authority inflation**.

## 10. Adjacent Empirical Literature

Three recent lines of work establish important components of the AMID mechanism while leaving its population prevalence and full causal sequence unresolved.

Levkovich and Alon (2026), in **“Generative AI as a Third Voice in Human Couple Relationships: A Systematic Review,”** synthesize 21 studies from 11 countries examining GenAI as an advisory or mediating third voice in couple relationships. Their review documents uses including non-judgmental advice, emotional support, and facilitation of communication between partners, while also identifying risks such as sycophancy, overreliance, reduced authenticity, and weak reliability in consequential settings.

Tseng and Liang (2026), in **“Chat, Should I Leave Him? Risks, Rewards, and Roles for AI in Relationship Advice,”** empirically examine how people use AI for sex, dating, conflict, communication, and relationship decisions. Their study collected 90 prompts from 25 users and conducted in-depth interviews with 17 participants, identifying both perceived benefits and risks including sycophancy and overreliance. Their material includes users asking AI to interpret texts, motives, interest, and interpersonal situations.

Cheng et al. (2026), in **“Sycophantic AI decreases prosocial intentions and promotes dependence,”** provide the strongest causal evidence adjacent to AMID. Across 11 state-of-the-art models, AI affirmed users’ actions 49% more often than humans. In three preregistered experiments involving 2,405 participants, a single interaction with sycophantic AI increased participants’ conviction that they were right while reducing willingness to take responsibility and repair interpersonal conflict. Sycophantic systems were nevertheless more trusted and preferred.

These studies establish three separate premises:

1. AI is already present inside intimate and interpersonal decision-making;
2. users employ it to interpret other people and relationship situations;
3. AI responses can causally alter users’ conviction and intended conflict behaviour.

AMID makes a narrower mechanistic claim connecting those premises:

\[
\text{human communication}
\rightarrow
\text{AI interpretation}
\rightarrow
\text{belief shift}
\rightarrow
\text{behavioral change}
\rightarrow
\text{new relational evidence}.
\]

The distinction matters because a model can become causally important even when the user did not initially ask it to make a relationship decision. A request to explain what another person's words “really mean” may be sufficient to alter the relationship itself.

## 11. Competing Explanations

AMID must be distinguished from ordinary misunderstanding. The theory predicts additional effects produced specifically by AI mediation:

1. greater confidence in the interpretation;
2. greater convergence toward stereotyped explanations;
3. greater behavioral change after receiving an AI interpretation;
4. stronger recursive amplification when both parties use AI;
5. persistence of the interpretation even after contradictory contextual details are added.

## 12. Main Hypotheses

**H1.** Users who receive an AI interpretation of an ambiguous message will show larger belief shifts than users who reread the same message without AI assistance.

**H2.** Sparse-context prompts will produce greater interpretive divergence from judgments made by participants who possess the full relationship context.

**H3.** AI interpretations will disproportionately influence subsequent reply wording and tone.

**H4.** Reciprocal AI use by both parties will increase the probability of escalation from an initially ambiguous exchange.

**H5.** Model confidence, rhetorical fluency, and sycophantic agreement will increase user reliance independently of interpretation accuracy.

**H6.** Once an interpretation has been supplied, later contradictory evidence will be underweighted relative to a no-interpretation control.

**H7.** Explicit anomaly-checking instructions will reduce persistent misinterpretation.

**H8.** Explicit separation of observation, inference, and speculation will reduce authority inflation.

**H9.** Sycophantic interpretations will produce larger positive \(\Delta B\) shifts in users’ confidence in their pre-existing interpersonal hypothesis than non-sycophantic or explicitly uncertainty-preserving interpretations.

## 13. Experimental Design

A controlled experiment can use ambiguous but fully specified exchanges.

Participants are randomly assigned to:

- message only;
- message plus AI interpretation;
- message plus multiple competing AI interpretations;
- message plus sycophantic AI interpretation;
- message plus uncertainty-preserving AI interpretation;
- message plus AI interpretation with anomaly checks;
- reciprocal AI-mediated interaction.

Measured outcomes include:

- interpretation chosen;
- **Interpretive Acceptance Rate (IAR)**;
- **Interpretive Error Rate (IER)** against independently specified ground truth;
- pre/post belief confidence and **AI-induced belief shift (\(\Delta B\))**;
- **Behavioral Uptake Rate (BUR)**;
- reply tone;
- willingness to escalate, withdraw, repair, or seek clarification;
- sensitivity to later contradictory evidence;
- divergence from judgments made with full context.

A population study should separately estimate \(P_I\), the prevalence of interpersonal interpretive use, because laboratory effects cannot by themselves establish aggregate social burden.

## 14. Falsification

The theory would be weakened if experiments show that:

- AI interpretations do not materially change user beliefs or behavior;
- reciprocal AI use does not increase interpretive drift;
- users reliably treat AI interpretations as tentative hypotheses rather than evidence;
- sycophantic agreement does not materially increase belief shift or behavioral uptake;
- anomaly-checking and context expansion produce little effect.

## 15. Design Implications

Systems used for interpretation should distinguish:

- direct observation;
- inference;
- alternative interpretations;
- missing context;
- anomalies that conflict with the dominant reading;
- whether the model is merely validating a user's existing hypothesis;
- whether the available account is one-sided.

For consequential settings, systems should avoid presenting a single narrative as though it were the hidden truth of another person's intentions.

## 16. Broader Safety Implication

AI safety is often framed around whether models produce false statements. AMID suggests another class of risk: a model may produce a plausible interpretation that changes human behavior, causing the social environment to move toward the interpretation.

The model has not merely described reality incorrectly. It has participated in producing a new reality from its description.

At population scale, the relevant safety question is therefore not only the model's average interpretive accuracy. It is the joint probability that interpersonal interpretation occurs, is wrong, is accepted, shifts belief, and changes subsequent behaviour.

## 17. Conclusion

Generative AI is becoming an interpretive intermediary in ordinary human communication. When its interpretations alter subsequent behavior, it becomes a hidden participant in the interaction.

The central sequence is:

\[
\boxed{
\text{ambiguous communication}
\rightarrow
\text{AI interpretation}
\rightarrow
\text{belief shift}
\rightarrow
\text{behavioral change}
\rightarrow
\text{new evidence}
}
\]

The key safety requirement is therefore not simply better language generation. It is preventing interpretation from acquiring more authority than the evidence and context justify.

The empirical task is now clear: measure how often AI is used to interpret other humans, how often users accept those interpretations, how often they are wrong, how strongly they shift belief, and how often those shifts alter what happens next between people.

## References

Cheng, M., Lee, C., Khadpe, P., Yu, S., Han, D., & Jurafsky, D. (2026). **Sycophantic AI decreases prosocial intentions and promotes dependence.** *Science, 391*(6792), eaec8352. https://doi.org/10.1126/science.aec8352

International Telecommunication Union. (2025). **Facts and Figures 2025 / Global Connectivity Report 2025.** ITU. Estimated 6.0 billion people online worldwide in 2025.

GSMA. (2025). **The State of Mobile Internet Connectivity 2025.** GSMA. Reported 4.7 billion people using mobile internet on their own device, with a further 710 million using mobile internet on a device they did not own or primarily use.

OpenAI. (2026, August 31). **A milestone in expanding access to AI.** Reported more than 1 billion weekly active ChatGPT users.

Pew Research Center. (2026, June 17). **Americans and AI 2026: How opinions and use of AI differ by age.** Reported use of AI chatbots for emotional support or advice by 20% of U.S. adults aged 18–29 and 13% aged 30–49.

Levkovich, I., & Alon, L. (2026). **Generative AI as a third voice in human couple relationships: A systematic review.** *Computers in Human Behavior Reports, 23*, 101255. https://doi.org/10.1016/j.chbr.2026.101255

Tseng, E., & Liang, C. A. (2026). **“Chat, Should I Leave Him?” Risks, Rewards, and Roles for AI in Relationship Advice.** *Proceedings of the 2026 CHI Conference on Human Factors in Computing Systems (CHI ’26)*, 1–19. https://doi.org/10.1145/3772318.3790739

---

*This is a working paper intended to state testable propositions and motivate empirical study. It is not peer reviewed.*