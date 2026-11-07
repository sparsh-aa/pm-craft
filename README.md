# pm-craft

A Claude Code / Claude Agent skill that makes Claude work like a trained product manager: PRDs and one-pagers,
problem framing, KPI trees and North Star metrics, user research, prioritisation, growth and GTM, A/B tests,
cohort and funnel analysis, RCA, guesstimates, tech and ML talk with engineers, design reviews, and PM case
interviews.

Built from structured PM training (shared with the course provider's permission) and widely published product
literature (Cagan, Torres, Balfour, Andrew Chen, Reforge, Petra Wille, Mixpanel, NN/g, and others).

## Install

```bash
git clone https://github.com/sparsh-aa/pm-craft ~/.claude/skills/pm-craft
```

Claude loads it automatically for PM-shaped tasks ("write a PRD for…", "what's the North Star for…",
"metric X dropped 10%…", "design X for Y").

## Layout

- `SKILL.md`: operating stance, routing table, default workflows, interview question types, quality bar.
- `references/01–09`: strategy and outcomes, discovery and research, problem framing and ideation, growth,
  metrics and experiments, artifacts and templates, tech and AI, design, worked cases.
- `references/index.md`: topic map and known gaps.
