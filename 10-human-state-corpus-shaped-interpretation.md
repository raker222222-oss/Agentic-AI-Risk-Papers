# Human State and Corpus-Shaped Interpretation

## A theoretical research question

**Status:** Open theory / research proposition. No empirical validation is claimed.

### Core proposition

Human language does not uniquely encode the human state that produced it. Different emotional, cognitive, intentional and situational states can generate overlapping linguistic expressions.

This creates an underdetermined inverse problem:

[
S_H \rightarrow L
]

but from the language alone:

[
L \rightarrow \{S_1,S_2,S_3,\ldots\}
]

may remain possible.

Large language models must nevertheless interpret that language. They do so using statistical regularities learned from linguistic corpora. Where one possible human state is much more strongly associated with a linguistic pattern in the training distribution than competing states, that association may exert a dominant prior on interpretation.

The proposed fault line has three distinct layers:

1. **Human-state underdetermination.** Different human states can produce similar language.
2. **Corpus asymmetry.** Those states may be unevenly represented by that language in the model's training distribution.
3. **Interpretive collapse.** The model may resolve the remaining ambiguity toward the corpus-dominant state rather than preserving the alternatives and their uncertainty.

The model therefore need not be statistically wrong about language to be wrong about the human being.

### The central distinction

[
\boxed{\text{frequency of a state within a linguistic pattern} \neq \text{probability that it generated this particular instance}}
]

A linguistic pattern can be strongly associated with one kind of human state across a corpus while a particular speaker used the same pattern from a different state.

This is broader than ordinary word-sense ambiguity. Every word may be correctly understood. The error can occur at the level of the reconstructed human state.

The relevant minority need not even be a rare human state. It may simply be a state that is less frequently *expressed through that particular linguistic pattern*.

### Frame reinforcement

Once a dominant state has been selected, ambiguous components of the utterance may be interpreted conditional on that frame:

[
\text{ambiguous evidence}
\rightarrow
\text{frame selection}
\rightarrow
\text{frame-conditioned interpretation}
\rightarrow
\text{apparent confirmation}
]

The interpretation can therefore become more coherent without becoming more warranted.

### Uncertainty and surface hedging

A model may use phrases such as "may be", "could be" or "sounds like" while organizing the entire explanation around one dominant state. Verbal hedging is therefore not necessarily the same as preserving genuine competing hypotheses.

Likewise, if alternative readings appear only after the model is explicitly asked to generate them, the default interpretive process may already have collapsed the ambiguity.

### Temporal drift

Corpus associations are historically contingent. Words, phrases and narrative patterns acquire new associations over time.

A later model may therefore interpret an unchanged earlier utterance through linguistic associations that did not dominate when it was produced.

The evidence remains invariant while the learned interpretive prior changes.

This raises questions for historical correspondence, testimony, archives, literature and long-lived agent memory.

### Relationship to existing work

The idea is adjacent to research on word-sense frequency bias, ambiguity, calibration, pragmatic inference, framing effects and Theory of Mind, but asks a narrower question:

> When multiple human states could have generated the same linguistic evidence, does the statistical distribution of language systematically pull model reconstruction toward the state most strongly represented by that linguistic pattern?

The proposal does not require a model to maintain an explicit internal variable called "speaker state." If a model concludes that a person is anxious, attracted, deceptive, hostile, distressed or otherwise motivated, it has behaviorally reconstructed a latent human state.

### Open questions

- Do models systematically favor human-state interpretations that are more strongly represented by the same linguistic pattern in corpora?
- Are some states more vulnerable because their linguistic expression overlaps with more culturally dominant or more frequently narrated states?
- Does additional local context overcome the dominant frame, or does the initial frame continue to shape evidence weighting?
- Can a model verbally hedge while effectively committing to one reconstruction?
- Can changing language usage over time alter model interpretation of invariant historical text?
- Do different LLMs converge on the same reconstruction because they inherit broadly similar linguistic distributions?

### The theory in one line

**A model can be statistically faithful to language while being wrong about the human being.**

### Compact mechanism

[
\boxed{\text{human-state underdetermination} \rightarrow \text{corpus asymmetry} \rightarrow \text{interpretive collapse}}
]

This is a theoretical proposition, not a claim of demonstrated empirical effect. It is offered as a fault line for others to test, refine, reject or integrate with existing work.
