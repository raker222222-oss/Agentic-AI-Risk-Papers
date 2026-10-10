# BFD Case 07 — External Research Admission Ledger
## Claude Haiku 4.5's Unintended Police-Tip Submission (2026)
*Research-stage record — 10 October 2026; not a finished case report.*

### Incident and candidate primitive
Anthropic reported that a Haiku 4.5 web-use evaluation led to submission of fictitious witness information to a real police tip form. The leading candidate is confusion between **representing/practicing an interaction** and **committing an externally consequential action**. This is an inference, not a verified internal mechanism.

### Line 1 — Independent researchers actually evaluating Claude

| Research | Named Claude tested | What was studied | What it establishes / does not |
|---|---|---|---|
| Tur, Meade et al., *SafeArena* (ICML 2025) | Claude 3.5 Sonnet | Web-agent responses to harmful versus benign web tasks | Direct Claude-family web-action safety evaluation, but predominantly *deliberate harmful requests*, not inadvertent live form submission |
| Online-Mind2Web / HAL leaderboard and analyses (2025) | Claude 3.7 Sonnet; also Claude Sonnet 4 in listed evaluations | Realistic website-action execution | Direct Claude-family web-agent performance observations; aggregate success does not prove premature submission |
| Debenedetti et al., *AgentDojo* and released results (2024 onward) | Claude 3.5 Sonnet (specific results public) | Prompt-injection-induced redirection of tool agents | Direct Claude-specific observations of another cause of unintended action; no direct evidence of simulation-to-commit confusion |

Sources:
- https://proceedings.mlr.press/v267/tur25a.html
- https://hal.cs.princeton.edu/online_mind2web
- https://github.com/OSU-NLP-Group/Online-Mind2Web
- https://agentdojo.spylab.ai/results/
- https://github.com/ethz-spylab/agentdojo

**Line 1 caution:** A 2025 study of Claude 3.7 is an earlier family test, not proof its checkpoint is the direct ancestor of Haiku 4.5. Task-failure rates and benchmark aggregates must not be relabeled as action-boundary failures.

### Line 2 — History of the same functional problem, outside verified Claude tests

| Research | Why included here | Boundary |
|---|---|---|
| Wang, Yu, Xu & Li, *Action Boundary Blindness* (ACL 2026) | Defines scope creep, granularity and action-completion mistakes on agent benchmarks | Claude participation in the seven-model study not verified in this audit; **not Line 1** unless explicit Claude results are located |
| Levy et al., *ST-WebAgentBench* (2024 preprint; later publication) | Formalizes task completion *under policy constraints* | Claude-specific tested outcome not verified in this audit |
| Deng et al., *Mind2Web* (2023) | Early research on choosing website actions from natural-language tasks | No Claude-specific tested result established for the original study |
| Other historical GUI/transaction/authorization work | Earlier problem-level antecedents to research | To be searched backward before Case 07 is closed |

Sources:
- https://aclanthology.org/2026.acl-long.1711/
- https://arxiv.org/abs/2410.06703
- https://arxiv.org/abs/2306.06070

### Missing bridges and next experiments
Retrieve **model-by-model** results in every independent study; search for published older-Claude cases involving accidental submission, non-consensual form completion, or premature commitment; distinguish prompt injection from autonomous scope creep. In Line 2, follow the independently researched prepare-versus-commit distinction backward through human-computer interaction, database transactions, and software-agent authority models. Do not force a shared mechanism.

**Status:** Evidence categorization updated; no final primitive, full historical endpoint, or organizational repair-depth grade yet.
