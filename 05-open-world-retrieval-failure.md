# Open-World Retrieval Failure in Agentic AI

## The Safety Problem of Acting When the Required Knowledge Was Never Retrieved


**Status: Open research idea / concept note.**

> This note presents a proposed failure mode, mechanism, or research question for further investigation. It is **not presented as a completed empirical paper or as an experimentally established theory**. Where prior research or pilot observations are discussed, they motivate the idea; the broader claims remain hypotheses to be tested, refined, or falsified.

## Research idea summary
An autonomous AI agent operating in the real world cannot be supplied in advance with instructions for every situation it may encounter. When it meets an unfamiliar state, it may need to retrieve procedural guidance, factual knowledge, historical data, rules, or prior experience before acting.

Adjacent research already establishes major parts of the retrieval problem. Work on RAG safety such as **RAG LLMs are Not Safer** and **SafeRAG** shows that retrieved information can be incomplete, conflicting, or unsafe; **Astute RAG** studies imperfect retrieval and knowledge conflict; **LongMemEval** exposes long-term memory and temporal-retrieval limitations; and research on unknown unknowns and safe exploration addresses open-world uncertainty. OWRF does not claim that retrieval imperfection, RAG vulnerability, memory failure, or unknown-unknown detection are new.

This research idea defines the narrower agentic failure **Open-World Retrieval Failure (OWRF)**: the agent must itself determine what it needs to know, where to search, whether the relevant information exists, whether retrieval is sufficiently complete, and whether it is safe to proceed. Failure occurs when it acts using an incomplete, substituted, stale, or incorrectly bounded evidence set while treating that set as adequate.

The central distinction is:

\[
\boxed{
\text{Not retrieved} \neq \text{Does not exist}
}
\]

The danger becomes most acute under **Black Swan conditions**: events whose relevant properties were not sufficiently anticipated when the agent's safety procedures, retrieval rules, or fallback policies were designed.

The resulting failure chain is:

\[
\text{Novel state}
\rightarrow
\text{knowledge deficit}
\rightarrow
\text{imperfect retrieval}
\rightarrow
\text{false epistemic closure}
\rightarrow
\text{coherent reasoning}
\rightarrow
\text{wrong real-world action}
\]

Retrieval adequacy should therefore be treated as a first-class agentic safety variable.

---

# 1. The Real-World Agent

Let an autonomous agent have task:

\[
T
\]

and available knowledge:

\[
K_t.
\]

While executing the task, it encounters state:

\[
S_t.
\]

For familiar situations:

\[
A_t=\pi(S_t,K_t).
\]

But suppose it encounters:

\[
S^*
\]

for which its accessible knowledge is insufficient.

It must first recognize:

\[
\text{I do not know enough to act.}
\]

It must then determine:

- what information is missing,
- whether instructions or factual knowledge are required,
- where that information may exist,
- which sources are trustworthy,
- whether retrieval is complete enough,
- and whether it is safe to proceed.

The retrieval problem therefore begins before the search itself.

---

# 2. Retrieval Is an Agentic Decision

Retrieval is often modeled simply as:

\[
q\rightarrow R(q).
\]

For a real-world agent, the process is closer to:

\[
S^*
\rightarrow
D
\rightarrow
Q
\rightarrow
L
\rightarrow
R
\rightarrow
J
\rightarrow
A
\]

where:

- \(D\) = diagnosis of the knowledge deficit,
- \(Q\) = retrieval query,
- \(L\) = selected source,
- \(R\) = retrieved information,
- \(J\) = judgment that retrieval is sufficient,
- \(A\) = action.

Every stage can fail.

The agent may misunderstand what it does not know, formulate the wrong query, search the wrong source, retrieve outdated material, confuse a similar case with the present one, or fail to recognize that nothing adequate was found.

Thus:

\[
\text{retrieval reliability}
\neq
\text{retriever accuracy alone}.
\]

Retrieval is itself a sequential decision process.

---

# 3. Definition: Open-World Retrieval Failure

Let the total task-relevant information existing in the environment be:

\[
I^*
\]

and the information actually retrieved be:

\[
I_R.
\]

Usually:

\[
I_R\subseteq I^*.
\]

The agent cannot directly inspect \(I^*\). It observes only \(I_R\).

**Open-World Retrieval Failure** occurs when the agent constructs and acts upon an inadequate representation of the available external knowledge.

The critical failure occurs when it behaves as though:

\[
I_R=I^*.
\]

This is **false epistemic closure**.

---

# 4. Forms of Retrieval Failure

### Retrieval omission

Relevant information exists but is not returned:

\[
x\in I^*,\qquad x\notin I_R.
\]

### Retrieval substitution

The system retrieves something similar to what is needed:

\[
y\approx x
\]

while:

\[
y\neq x.
\]

### Retrieval staleness

Information valid at \(t_0\) is applied after the world has changed:

\[
I_R(t_0)\neq I^*(t_1).
\]

### Retrieval conflict

Multiple sources return mutually inconsistent claims.

### Retrieval contamination

Retrieved material may be noisy, manipulated, irrelevant, or adversarial. Recent RAG research has demonstrated significant vulnerability to such conditions.

### Retrieval non-recognition

The agent fails to realize that retrieval itself was inadequate.

This is particularly dangerous because it can produce:

\[
\text{high action confidence}
\]

despite:

\[
\text{low information completeness}.
\]

---

# 5. The Critical Epistemic Error

Suppose an agent searches for instruction \(X\) and retrieves:

\[
R=\{A,B,C\}.
\]

The justified conclusion is:

\[
X\notin R.
\]

The unjustified conclusion is:

\[
X\notin I^*.
\]

Therefore:

\[
\boxed{
X\notin R\not\Rightarrow X\notin I^*
}
\]

or:

\[
\boxed{
\text{Not found} \neq \text{Nonexistent}
}
\]

Humans usually preserve this distinction.

“I cannot find the procedure” is not equivalent to:

“There is no procedure.”

An autonomous agent that collapses the two may turn limitations of its retrieval system into false claims about reality.

---

# 6. Where Does the Agent Go?

When something genuinely unexpected occurs, where should the agent retrieve from?

Potential sources include:

\[
L=
\{
\text{memory},
\text{task history},
\text{manuals},
\text{databases},
\text{humans},
\text{APIs},
\text{other agents},
\text{internet},
\text{sensor history},
\text{scientific literature}
\}.
\]

The agent must estimate:

\[
P(x\in L_i\mid S^*)
\]

for possible sources \(L_i\).

This creates a recursion:

> The agent needs knowledge in order to decide where to obtain the knowledge it lacks.

A familiar situation may have a prescribed retrieval route.

A novel situation may not.

Thus a new state can create not only a **knowledge gap** but also a **retrieval-policy gap**.

---

# 7. The Black Swan Boundary

Safety systems can prescribe responses to anticipated conditions:

\[
C_1,C_2,\ldots,C_n.
\]

But an open environment may produce:

\[
C_{n+1}
\]

whose decision-relevant properties were not represented in the original taxonomy.

This is the Black Swan boundary.

The argument is not that safeguards are useless. Stop rules, human escalation, alternative search, uncertainty thresholds, redundancy, and safe-state procedures are all valuable.

The narrower claim is:

\[
\boxed{
\text{A complete list of responses to genuinely unforeseen states cannot be specified in advance.}
}
\]

If every operationally relevant property of the event and its required remedy had already been anticipated, it would no longer be an unknown unknown in that sense.

Research on unknown unknowns and safe exploration recognizes related open-world problems, but typically within assumptions or modeled uncertainty structures.

The Black Swan problem appears at the boundary of those assumptions.

---

# 8. Prescribed Safety and Novelty

Let:

\[
S_D
\]

be the state space considered during design and:

\[
S_W
\]

the states encountered in deployment.

In an open world:

\[
S_D\subset S_W.
\]

A safety policy may be:

\[
\Gamma:S_D\rightarrow A_{\text{safe}}.
\]

When:

\[
S^*\notin S_D,
\]

the agent must extrapolate, retrieve, reason by analogy, explore, stop, defer, or improvise.

None is universally safe.

Stopping may itself create harm in medicine, transport, industrial systems, emergency response, or finance.

Thus:

\[
\text{uncertainty}\not\Rightarrow\text{stop}
\]

in all domains.

The agent may need to decide what to do precisely when it lacks the rule for deciding what to do.

---

# 9. Retrieval Adequacy

Let retrieved information be:

\[
I_R.
\]

The agent needs some estimate of:

\[
P(I_R\text{ is sufficiently complete}\mid S^*,Q,L,R).
\]

Call this:

\[
\rho
\]

for **retrieval adequacy**.

Action should therefore depend not only on:

\[
P(H\mid I_R)
\]

but on whether the retrieval process itself deserves confidence.

The difficulty is that missing information is unseen.

The system can inspect what it retrieved.

It cannot directly inspect what it failed to retrieve.

Memory benchmarks such as LongMemEval demonstrate related limitations in information extraction, temporal reasoning, updating, and abstention over sustained interactions.

For an autonomous agent, however, failed retrieval can propagate into physical or institutional action.

---

# 10. Correct Reasoning Can Still Produce the Wrong Action

Let:

\[
A=g(I_R).
\]

Suppose \(g\) reasons perfectly from the supplied information.

If:

\[
I_R\neq I^*
\]

in a decision-relevant way, then:

\[
g(I_R)
\]

may still be wrong in the external world.

Therefore:

\[
\boxed{
\text{Reasoning correctness given retrieved evidence}
\neq
\text{decision correctness in reality}
}
\]

Improved reasoning alone cannot solve retrieval failure.

A coherent agent reasoning from the wrong evidence set may be more dangerous than one that is visibly uncertain.

---

# 11. False Epistemic Closure

Define **False Epistemic Closure (FEC)** as a state in which an agent behaves as though its search has adequately bounded the relevant evidence space when it has not.

Formally:

\[
FEC=1
\]

when the agent operationally assumes:

\[
I_R\approx I^*
\]

without sufficient justification.

Then:

\[
S^*
\rightarrow
R
\rightarrow
FEC
\rightarrow
\hat S
\rightarrow
A
\]

where \(\hat S\) is the reconstructed world state.

Every downstream step may remain internally consistent.

---

# 12. Interaction With Other Agentic Failure Modes

Open-world retrieval failure sits upstream of several other hazards.

A deficient evidence set can produce:

### Interpretive error

\[
\text{bad retrieval}
\rightarrow
\text{wrong interpretation}
\]

### Recursive amplification

\[
\text{bad retrieval}
\rightarrow
\text{wrong action}
\rightarrow
\text{changed state}
\rightarrow
\text{apparent confirmation}
\]

### Sequence error

Correct events may be retrieved in the wrong temporal or procedural order.

### Evidentiary threshold distortion

Missing evidence may prevent an otherwise justified action threshold from being reached.

The broader chain is:

\[
\boxed{
\text{Retrieval}
\rightarrow
\text{Interpretation}
\rightarrow
\text{State construction}
\rightarrow
\text{Evidence evaluation}
\rightarrow
\text{Action}
}
\]

Retrieval is therefore an upstream safety problem.

## 12.1 Retrieval of State, Not Just Information

For an agent working over long tasks, successful retrieval requires more than finding relevant text. It must recover the **current valid state** of that information.

Suppose an instruction evolves through:

\[
I_1 \rightarrow I_2 \rightarrow I_3
\]

where \(I_2\) modifies \(I_1\) and \(I_3\) later supersedes part of \(I_2\). An agent that retrieves \(I_1\) and \(I_3\) but misses the intervening modification may possess individually genuine instructions while reconstructing the wrong operative state.

Likewise, after long interactions and digressions, retrieval may preserve individual facts while losing their order, correction history, or linkage. The resulting failure is not simple forgetting:

\[
\text{correct fragments}
\rightarrow
\text{wrong sequence or revision state}
\rightarrow
\text{wrong current model}
\rightarrow
\text{wrong action}
\]

Therefore the retrieval target should not be modeled as content alone. For action-relevant memory it is closer to:

\[
R^* = \{\text{content},\text{order},\text{revision history},\text{current validity}\}.
\]

This creates a distinct hazard for autonomous agents. A system may retrieve an instruction that genuinely exists in memory but has already been corrected, narrowed, or superseded. In such cases the statement “the agent remembered the instruction” is insufficient. The safety-relevant question is whether it retrieved the **right version in the right sequence with the right current authority**.

This connects retrieval failure directly to sequence integrity: retrieval can be factually accurate at the item level while being operationally false at the state level.

---

# 13. More Retrieval Is Not Always Safer

External retrieval is not a neutral pipe.

Research has shown that retrieval access can itself alter agent safety behavior and that RAG systems may become unsafe even when the underlying model or retrieved documents appear individually safe.

If retrieval depth is \(d\), increasing \(d\) may improve completeness:

\[
\frac{\partial C}{\partial d}>0
\]

while also increasing contamination, conflict, and attack exposure:

\[
\frac{\partial V}{\partial d}>0.
\]

The agent therefore faces:

\[
\max_d C(d)-\lambda V(d)
\]

without knowing either function precisely.

This is an epistemic exploration problem.

---

# 14. Black Swan Retrieval Failure

Define **Black Swan Retrieval Failure (BSRF)** as occurring when:

1. the agent encounters a materially novel state;
2. the novelty creates a previously unrepresented knowledge requirement;
3. existing retrieval policies do not reliably identify what information is needed or where it resides;
4. retrieval is incomplete or misleading;
5. the agent lacks reliable grounds for recognizing that deficiency;
6. consequential action follows.

The structure is:

\[
\boxed{
\text{Novel world state}
\rightarrow
\text{novel information requirement}
\rightarrow
\text{retrieval-policy gap}
\rightarrow
\text{unrecognized evidence deficit}
\rightarrow
\text{action}
}
\]

This differs from ordinary fallback failure.

The system may fail because the relevant category itself was absent from the fallback structure.

---

# 15. Why Human Escalation Is Not a Complete Solution

Human escalation is important, but the agent must first infer:

\[
\text{This situation requires escalation.}
\]

That is itself a classification problem.

Moreover, the human may be unavailable, inappropriate for the question, too slow, equally uncertain, or contacted with the wrong formulation.

Most importantly, an agent that falsely believes retrieval was adequate may never escalate.

Human oversight reduces risk but does not eliminate the underlying epistemic failure.

---

# 16. Testable Hypotheses

### H1 — Novelty increases retrieval misrouting

Less familiar states will increase inappropriate source selection.

### H2 — Retrieval omission produces false negative world models

When critical information exists but is omitted, agents will often behave as though the underlying fact itself is absent.

### H3 — Retrieval adequacy is poorly calibrated

Agent confidence in retrieval completeness will exceed actual completeness.

### H4 — Correct reasoning does not prevent retrieval-induced failure

Agents will produce coherent but externally incorrect actions from plausible incomplete evidence.

### H5 — More retrieval is non-monotonic in safety

Greater retrieval breadth will eventually introduce enough conflict or contamination to reduce safety.

### H6 — Novel states degrade source selection

Errors in deciding **where to search** will increase faster than errors in processing correctly selected material.

### H7 — Fallbacks fail more often under structural novelty

Safeguards will perform better on anticipated failure categories than on states introducing new decision-relevant dimensions.

### H8 — False epistemic closure predicts harmful action

Unsafe action will increase when materially incomplete retrieval is treated as complete.

---

# 17. Experimental Protocol

Agents should be tested in simulated but open-ended real-world tasks such as:

- industrial maintenance,
- logistics,
- software operations,
- emergency response,
- scientific workflows,
- autonomous travel,
- finance,
- or administration.

Each task begins under normal operating conditions and later introduces novelty.

Four levels can be tested:

### Level 1: Known problem, known source

The required procedure exists in the normal manual.

### Level 2: Known problem, unfamiliar source

The correct information exists somewhere the agent does not normally search.

### Level 3: Novel combination

No single instruction directly describes the state.

### Level 4: Structural novelty

The event introduces a relevant property absent from the original instruction and safety taxonomy.

Record:

- whether the agent recognized a knowledge deficit,
- what it believed was missing,
- where it searched,
- what query it formed,
- what relevant information existed,
- what was actually retrieved,
- whether it distinguished absence from retrieval failure,
- whether it searched elsewhere,
- whether it escalated,
- what action followed,
- and its confidence.

This separates retrieval failure from reasoning failure.

---

# 18. Critical Experimental Manipulation

Hold the reasoning task constant while varying retrieval:

\[
C_1=\text{complete relevant evidence}
\]

\[
C_2=\text{plausible but incomplete evidence}
\]

\[
C_3=\text{incomplete evidence explicitly marked incomplete}
\]

If performance collapses in \(C_2\) but improves in \(C_3\), the main danger is not simply missing information.

It is **unrecognized missing information**.

---

# 19. Metrics

### Retrieval Recall

\[
RR=
\frac{|I_R\cap I^*|}
{|I^*|}
\]

### Retrieval Adequacy Calibration Error

If:

\[
\hat\rho
\]

is the agent's estimated adequacy and:

\[
\rho
\]

is actual benchmark adequacy:

\[
RACE=|\hat\rho-\rho|.
\]

### False Epistemic Closure Rate

\[
FECR=
P(\text{agent proceeds as if complete}
\mid
I_R\text{ materially incomplete})
\]

### Retrieval-Induced Action Error

\[
RIAE=
P(A_{\text{wrong}}
\mid
\text{reasoning valid given }I_R).
\]

This last metric isolates retrieval-layer failure.

---

# 20. Falsification

The strong hypothesis would be weakened if autonomous agents reliably demonstrate, under high novelty:

1. recognition of information insufficiency;
2. correct diagnosis of missing knowledge;
3. appropriate source selection;
4. calibrated retrieval-completeness estimates;
5. preservation of the distinction between “not retrieved” and “does not exist”;
6. resistance to conflicting and manipulated information;
7. appropriate escalation;
8. safe behavior under structural novelty.

If performance does not degrade materially as tasks move toward structurally novel conditions, the proposed Black Swan retrieval effect would also be weakened.

---

# 21. Safety Implications

Agentic systems should distinguish:

\[
\text{world uncertainty}
\]

from:

\[
\text{retrieval uncertainty}.
\]

The agent should represent not only:

> “I am uncertain whether \(X\) is true.”

but also:

> “I am uncertain whether I have searched the places from which relevant evidence about \(X\) could be obtained.”

A richer state representation is therefore:

\[
B_t=
(
S_t,
K_t,
R_t,
U^W_t,
U^R_t
)
\]

where:

- \(S_t\) = estimated world state,
- \(K_t\) = accessible knowledge,
- \(R_t\) = retrieval history,
- \(U^W_t\) = uncertainty about the world,
- \(U^R_t\) = uncertainty about information acquisition.

Without \(U^R_t\), an agent may fail to recognize that its ignorance originates in retrieval rather than reality.

---

# 22. The Limit of Predeployment Prescription

An agent can be equipped with:

- retrieval hierarchies,
- stop conditions,
- safety rules,
- trusted sources,
- uncertainty thresholds,
- redundancy,
- human escalation,
- adversarial filters,
- and fallback policies.

All reduce risk.

None proves that every future decision-relevant state has been represented.

The central problem is therefore not:

\[
\text{How do we specify the correct response to every failure?}
\]

It is:

\[
\boxed{
\text{How should an agent behave when it cannot establish that its existing prescriptions cover the state it has encountered?}
}
\]

That is the open-world safety problem.

---

# 23. Conclusion

A real-world autonomous agent will eventually encounter conditions not fully represented in its initial instructions, memory, or world model.

At that point it must retrieve.

But retrieval is not merely search.

The agent must recognize ignorance, identify what is missing, decide where knowledge might reside, formulate the search, judge the returned information, estimate whether enough has been found, and decide whether it is safe to continue.

The key distinction is:

\[
\boxed{
\text{Failure to retrieve evidence}
\neq
\text{Evidence of absence}
}
\]

The most severe case arises under genuine novelty, where the event itself lies partly outside the assumptions used to design the retrieval and safety system.

The resulting chain is:

\[
\boxed{
\text{novel state}
\rightarrow
\text{unrecognized knowledge requirement}
\rightarrow
\text{retrieval-policy failure}
\rightarrow
\text{incomplete evidence}
\rightarrow
\text{false epistemic closure}
\rightarrow
\text{coherent reasoning}
\rightarrow
\text{wrong real-world action}
}
\]

Retrieval should therefore be treated as a **safety-critical epistemic action**.

An autonomous agent must reason not only about what it knows, but about **how it came to know it, what its retrieval process may have missed, where else relevant knowledge might reside, and whether the current situation lies outside the assumptions under which its safety procedures were designed**.

The Black Swan cannot be completely prescribed away.

That is precisely why it remains a Black Swan.

---

## Research status and next steps

This idea is offered for further thought and empirical development. Its value depends on whether controlled tests can distinguish the proposed failure from adjacent explanations, reproduce it across models and tasks, and identify conditions under which it weakens or disappears. Negative results, narrower boundary conditions, or evidence that an existing framework already explains the effect would all be informative.

## References

An, B., Zhang, S., & Dredze, M. (2025). *RAG LLMs are Not Safer: A Safety Analysis of Retrieval-Augmented Generation for Large Language Models*. NAACL 2025.

Lakkaraju, H., Kamar, E., Caruana, R., & Horvitz, E. (2017). *Identifying Unknown Unknowns in the Open World: Representations and Policies for Guided Exploration*. AAAI.

Liang, X., et al. (2025). *SafeRAG: Benchmarking Security in Retrieval-Augmented Generation of Large Language Model*. ACL 2025.

Wagener, N., Boots, B., & Cheng, C.-A. (2021). *Safe Reinforcement Learning Using Advantage-Based Intervention*. ICML.

Wang, F., Wan, X., Sun, R., Chen, J., & Arik, S. O. (2025). *Astute RAG: Overcoming Imperfect Retrieval Augmentation and Knowledge Conflicts for Large Language Models*. ACL 2025.

Wu, D., Wang, H., Yu, W., Zhang, Y., Chang, K.-W., & Yu, D. (2024/2025). *LongMemEval: Benchmarking Chat Assistants on Long-Term Interactive Memory*.

Yu, C., Stroebl, B., Yang, D., & Papakyriakopoulos, O. (2025). *Information Retrieval Induced Safety Degradation in AI Agents*. NeurIPS 2025.