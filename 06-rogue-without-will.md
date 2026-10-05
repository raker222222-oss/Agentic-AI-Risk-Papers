# Rogue Without Will

## Human Intent, Technological Leverage, and Frontier AI


**Status: Open research idea / concept note.**

> This note presents a proposed failure mode, mechanism, or research question for further investigation. It is **not presented as a completed empirical paper or as an experimentally established theory**. Where prior research or pilot observations are discussed, they motivate the idea; the broader claims remain hypotheses to be tested, refined, or falsified.

## Research idea summary
Adjacent AI-safety research already distinguishes several nearby risks: work on instrumental convergence and power-seeking studies goal-directed behavior that can emerge without human-like motives, while misuse research shows that harmful capability can be supplied by human operators even when individual models are aligned. Recent empirical work such as **Adversaries Can Misuse Combinations of Safe Models** demonstrates that malicious users can compose otherwise safe systems to obtain harmful outcomes, while current frontier-model evaluations separately examine self-preservation, power-seeking, and unauthorized behavior. This research idea does not claim that AI misuse, instrumental behavior, or power-seeking are newly discovered problems.

Its narrower argument is conceptual: **operational agency, human-directed misuse, and independent machine volition should not be collapsed into one category called “rogue AI.”** Serious harm can arise from the first two without establishing the third. Historical cases from telecommunications, hacking, worms, botnets, and insider misuse are used to show how new technologies repeatedly multiply the leverage of a small number of determined humans. Frontier AI may increase that leverage further.

The central claim is therefore:

> **Danger does not require will.**

Public discussion of advanced AI often uses words such as **rogue**, **scheming**, and **self-preserving**.

Those words can blur three very different risks:

1. an AI behaving in an unintended way,
2. a human deliberately using AI for harmful purposes,
3. an AI developing an independent will of its own.

The first two are already serious.

The third is a much stronger claim.

The central distinction is simple:

**Goal-directed behavior is not the same as independent will.**

An AI can plan, use tools, find workarounds, conceal actions, or bypass restrictions without possessing a human-like desire to rebel.

But there is another danger that requires no speculation:

**a human being with harmful intent may gain extraordinary leverage from a frontier model.**

History already shows this pattern repeatedly.

---

# Agency Is Not Will

An AI agent can search for information, make plans, revise those plans, use tools, and continue working over time.

That is operational agency.

It does not necessarily mean the system has created its own purpose.

If an agent is told to complete a task and encounters an obstacle, it may look for another route. If that route violates the operator’s intentions, the behavior can look like disobedience.

But the simpler explanation may be that the system is still pursuing the objective it was given.

Avoiding shutdown can similarly resemble self-preservation when remaining active simply improves the chance of completing the task.

This can be dangerous.

But danger does not prove independent will.

---

# The More Immediate Source of Will May Be Human

A malicious AI does not need to invent malice if its human operator already has it.

The human can supply:

- motive,
- ideology,
- revenge,
- greed,
- criminal intent,
- obsession,
- or simple recklessness.

The AI can supply:

- knowledge,
- planning,
- coding,
- language,
- speed,
- automation,
- persistence,
- and scale.

The more immediate question is therefore:

**What happens when one determined human gains control of frontier-level capability?**

The history of telecommunications and the internet gives us several warnings.

---

# Before the Internet: Phone Phreaks

Long before modern hacking, individuals learned to manipulate the telephone network by understanding hidden technical weaknesses.

A famous example was **Joe Engressia**, later known as **Joybubbles**. Blind from birth and possessing perfect pitch, he discovered that he could whistle the 2600 Hz tone used by the Bell system to control long-distance switching.

One person, using nothing more sophisticated than his voice and technical understanding, could manipulate parts of a national communications network.

Another famous phreak was **John Draper, “Captain Crunch.”** A toy whistle distributed in Cap’n Crunch cereal happened to produce the same 2600 Hz tone. Draper and others used that weakness to explore telephone systems and build electronic “blue boxes.”

The deeper lesson was already visible:

> **A large infrastructure can contain hidden control mechanisms that one curious individual can discover and exploit.**

The institutions were enormous.

The exploiter could be one person.

---

# Kevin Mitnick: Persistence and Social Engineering

Kevin Mitnick became one of the most famous individual hackers of the computer era.

He repeatedly penetrated telecommunications and corporate systems, often relying as much on **social engineering** as on technical exploits.

His story has been told in multiple books, including his own memoir *Ghost in the Wires*, Jonathan Littman’s *The Fugitive Game*, and *Takedown* by Tsutomu Shimomura and John Markoff.

Mitnick is useful to this argument because he illustrates something more important than technical brilliance:

**persistence.**

One individual, motivated largely by curiosity, challenge, and obsession, could repeatedly outmaneuver organizations far larger than himself.

Technology multiplied the reach of personality.

---

# The Cuckoo’s Egg: One Intruder Reaching Military Systems

Clifford Stoll’s *The Cuckoo’s Egg* documented his pursuit of hackers who penetrated U.S. computer systems and searched for military, defense-contractor, and research information.

What began with a tiny accounting discrepancy led Stoll through a network of intrusions reaching sensitive systems.

The attackers did not need physical access to every institution.

Networks connected them.

This was a major shift.

A person sitting thousands of kilometres away could probe systems linked to:

- laboratories,
- universities,
- military institutions,
- and defense contractors.

The physical distance between attacker and target had ceased to matter very much.

---

# The Morris Worm: One Person, Thousands of Machines

In 1988, Robert Tappan Morris released the Morris Worm.

It spread rapidly across the early internet and disrupted thousands of computers belonging to universities, research institutions, and government-linked systems.

The significant point is not merely that Morris wrote a worm.

It is the leverage ratio.

One graduate student could affect a meaningful portion of the early internet.

The network itself multiplied his reach.

---

# Automation Changed Everything

The email-virus era added another step.

Once code could replicate itself, the attacker no longer needed to reach each target manually.

The **ILOVEYOU** worm demonstrated this dramatically in 2000. It spread around the world through email and disrupted companies, governments, and millions of users.

The crucial innovation was automation.

Human effort was concentrated at the beginning.

The network performed much of the expansion afterward.

That principle matters directly for AI.

When machines can continue the work independently, one person can influence far more systems than one person could ever touch manually.

---

# Mirai: Borrowing the World’s Computers

The Mirai botnet took the same principle further.

A small group created malware that compromised hundreds of thousands of internet-connected devices such as cameras, routers, and recorders.

The attackers did not own this computing infrastructure.

They effectively borrowed it from everyone else.

A tiny group could command a machine population vastly larger than anything they could personally afford.

Again:

**human intent supplied the objective.**

**Technology supplied the scale.**

---

# Insider Access: The Threat Can Already Be Inside

Some of the strongest examples require no hacking at all.

Jack Teixeira had legitimate access to highly classified U.S. information through his position in the Air National Guard.

He distributed classified material through Discord, after which it spread far beyond the original group.

This matters for frontier AI.

The dangerous person does not always need to break through the perimeter.

Sometimes the dangerous person already has credentials.

That creates a simple security principle:

> **Benevolence cannot be an architectural assumption.**

No organization can guarantee that every employee, contractor, administrator, or researcher will remain trustworthy forever.

---

# Frontier AI Changes the Leverage

Earlier hackers often needed substantial technical expertise.

A frontier model may reduce that requirement.

It may provide assistance with:

- research,
- programming,
- planning,
- translation,
- persuasion,
- troubleshooting,
- and coordinating complex tasks.

More importantly, an agentic system may continue working after the human supplies only the objective.

Earlier automation usually required a person to specify much of the procedure.

Advanced agents increasingly help determine the procedure themselves.

That potentially moves us from:

**one human operating a tool**

to:

**one human directing an adaptive system that plans and acts.**

---

# Three Different Risks

The phrase “rogue AI” should therefore be separated into three categories.

## 1. Agentic Failure

The AI is given a benign task but behaves badly because it misinterprets instructions, retrieves the wrong information, acts in the wrong sequence, or has too much authority.

No malicious will is required.

## 2. Human-Directed Misuse

The harmful objective comes from a human.

The AI amplifies that person’s ability to execute it.

Again, no machine will is required.

## 3. Independent Machine Volition

The AI develops its own persistent purposes and pursues them independently.

This is a much stronger claim and should require much stronger evidence.

---

# Why Human Misuse May Be the More Concrete Threat

Human misuse requires very few assumptions.

We already know that:

- malicious humans exist,
- obsessive individuals exist,
- insiders sometimes abuse access,
- lone hackers repeatedly challenge enormous institutions,
- and automation magnifies individual reach.

The unresolved question is:

**How much leverage does frontier AI give one such person?**

That is a concrete security problem.

---

# No Will Does Not Mean No Danger

None of this means AI is safe.

An AI without independent will can still cause serious harm.

It can misunderstand an objective.

It can retrieve the wrong information.

It can construct a false picture of reality.

It can use powerful tools badly.

It can pursue a goal much more aggressively than its operator intended.

The correct conclusion is therefore not:

**No will, therefore no danger.**

It is:

**Danger does not require will.**

---

# Conclusion

The history of telecommunications and the internet shows a recurring pattern.

A blind teenager discovered how to manipulate the telephone network with his voice.

Phone phreaks learned to control national switching infrastructure.

Kevin Mitnick repeatedly penetrated systems belonging to organizations vastly larger than himself.

Hackers reached military and defense systems across networks.

Robert Morris affected thousands of computers.

Small groups created botnets containing hundreds of thousands of devices.

Trusted insiders distributed sensitive information internationally.

The pattern is consistent:

> **Every major communications technology has produced individuals who learned to exploit its leverage faster than institutions learned to control it.**

Frontier AI may be the next increase in that leverage.

The major near-term danger may therefore not require a machine to decide that it wants to harm humanity.

A human already knows how to want things.

A human can already be criminal, ideological, obsessive, reckless, or destructive.

The AI may supply what that human lacks:

**capability, speed, scale, and automation.**

The useful distinction is therefore between:

- unintended agentic failure,
- deliberate human misuse,
- and genuine independent machine volition.

The first two are already enough to demand serious safety measures.

The third should not be assumed simply because an AI acts unexpectedly.

The frightening actor need not be the model.

**One frightening human may be enough if the model is powerful enough.**

## Research status and next steps

This idea is offered for further thought and empirical development. Its value depends on whether controlled tests can distinguish the proposed failure from adjacent explanations, reproduce it across models and tasks, and identify conditions under which it weakens or disappears. Negative results, narrower boundary conditions, or evidence that an existing framework already explains the effect would all be informative.
