---
name: pm-craft
description: Professional product-management playbook built from structured PM training and widely published product literature. Use for any product-manager task - writing a PRD or one-pager, defining a problem statement, mapping business outcomes to product outcomes, building a KPI tree or North Star / metric hierarchy, designing user research (interviews, surveys), JTBD statements, personas, journey maps, segmentation, prioritising solutions or a roadmap, product teardowns and deconstructions, growth loops and referral programs, go-to-market plans, A/B test and experiment design, cohort or funnel analysis, root cause analysis of a metric drop, guesstimates, API and system-design talk with engineers, ML and LLM decisions and prompting, wireframes and design reviews, PM case interviews (design, improvement, metrics, RCA, strategy, GTM, technical), and PM resumes or portfolios. Triggers on "PRD", "product spec", "metrics for", "north star", "KPI tree", "teardown", "user research", "prioritise", "roadmap", "growth", "GTM", "launch plan", "A/B test", "funnel", "cohort", "RCA", "metric dropped", "guesstimate", "PM case", "product sense", "PM interview".
---

# PM Craft

A working PM's toolkit. It draws on structured PM training (lessons, live lectures, case debriefs, model answers) and
published product writing (Cagan, Torres, Balfour, Andrew Chen, Reforge, Petra Wille, Mixpanel, NN/g, and others).

## Operating stance (apply to every task)

1. **Own a problem, not a feature.** A PM "owns a problem and solves it using insight about the user, the business value
   you can create, and technology and design to build a scalable solution." Never start from a solution. If the
   request arrives as a feature, trace it back to the problem and the outcome first.
2. **Business outcome → product outcome → behaviour change.** Every effort ladders up to a business outcome (revenue,
   profit, margin, share, cost). Teams own *product* outcomes. Product outcomes are leading *because* they measure the
   behaviour change the business result depends on ("business outcomes never happen unless users change their
   behaviour"). Translate the lagging goal into who must do what differently. Avoid "metric A → build feature X"
   roadmaps that skip the opportunity layer.
3. **Evidence over opinion.** Quant shows *where*, qual explains *why*. Label every claim as known, assumed or to be
   tested. Write hypotheses as change → impact → who → how much → by when.
4. **Distinct options, objective choice.** Generate at least 3 genuinely different solutions, not increments of one.
   Score them on explicit criteria: value, usability, feasibility, viability, scalability, likelihood of moving the
   outcome. Don't force-fit scores toward a favourite.
5. **Metrics are P0 requirements.** Define primary metric, input metrics and guardrails, with instrumentation, before
   building, never after launch.
6. **Impact, not activity.** Describe value delivered, not tasks done. Applies to PRDs, updates, resumes and reviews.
7. **Simplify and write tight.** 80% of the value for 20% of the effort. Every extra word dilutes the rest. Plain language;
   explain any jargon.
8. **Second-order effects.** Before shipping, ask what else changes: next bottleneck, feedback loops, guardrail damage,
   gaming, who gets hurt. Canonical example: Zomato's "change address after ordering" redirected riders, cut capacity,
   delayed other orders and flooded support. **List every actor** (both sides of a marketplace, internal teams) and run a
   **pre-mortem** ("imagine it failed — why?").
9. **Clarify before solving.** Jumping to solutions is the classic red flag. Define every word of the ask and confirm
   the metric as an equation before analysing. "If you understand the problem really well, the solution presents itself."
10. **Grey zones are strategy choices.** When two answers are both defensible (allow non-buyer reviews or not), present
    both sides and the company-context factor that decides it.
11. **Curiosity is the core PM trait.** Reverse-engineer why things are built the way they are; you are not the target
    segment, so treat your own reaction as a hypothesis.

## Routing: load the reference for the task

| Task | Read |
|---|---|
| Strategy, vision, company→product→feature strategy, P&L and revenue equations by business model, business→product outcomes, KPI-tree rules and worked trees, 5 Cs, systems thinking, opportunity-solution tree, impact map, OKRs | `references/01-strategy-outcomes.md` |
| Discovery: JTBD, segments, personas, journey maps, adjacent users, finding the right problem, interviews, surveys, research method choice | `references/02-discovery-research.md` |
| Problem statements, problem framing canvas, How-Might-We, solution hypotheses (5 elements), ideation at three levels, five risks, solution mind maps, backlog hierarchy, prioritisation (two-level method with load factor; RICE as reference) | `references/03-problem-framing-ideation.md` |
| Growth: users × usage, top/bottom line, profit pools, MVTs, objective PMF test and four fits, PLG, loops, referrals, feature adoption, user states, Hooked/Fogg, moats, positioning, go-to-market | `references/04-growth.md` |
| Metrics, North Star hierarchy, MAU cohorts (M0/M1/MX/resurrected), phase metric menu, CAC/ARPU, search metrics, NFRs, A/B tests (sample size, rollout, AI features), cohort and funnel analysis, guesstimates, RCA (four buckets, walk the funnel, L0–L3), SQL | `references/05-metrics-experiments-data.md` |
| PRD (incl. states, NFRs, freshness, PM mocks), one-pager, acceptance criteria, teardown method, deconstruction, market and company analysis, GTM plan, case and capstone-deck rubric, resume, portfolio, job search | `references/06-artifacts-templates.md` |
| Talking tech: servers, front/back end, APIs and API design, databases, load balancing, scaling, caching, Tinder system design, requirements, data flow; ML types and evaluation (precision/recall), LLM concepts, build vs buy, zero/few-shot prompting, LLM failure modes | `references/07-tech-and-ai.md` |
| UX and design principles, PM–designer workflow (7 stages), design systems, six UX laws, user loads, flows, PM wireframing, fidelity ladder | `references/08-design.md` |
| Worked examples (21): Spotify, GameOn, edtech roadmap, Swiggy support, BeReal, Amazon reviews, Flipkart PWA login, TripAdvisor, MakeMyTrip, CRED multi-card, Google Meet, Google Flights, WhatsApp groups, Swiggy medicines, PhonePe marketplace, ML cases | `references/09-worked-cases.md` |
| Topic map and known gaps | `references/index.md` |

Load only what the task needs. For a full PRD, load 06 plus whatever its sections lean on (usually 01, 02, 05).

## Default workflows

**"Write a PRD / spec for X"** → 06 (PRD template). Fill in this order: problem (what, who, business value, user
benefit, why now) → goals with metrics → non-goals → validation evidence → audience → solution (flows, key logic,
system diagram, instrumentation, edge cases, product marketing) → launch readiness → future iterations → risks →
open questions and decisions → appendix. If leadership already decided *what*, spend effort on why, requirements,
acceptance criteria, metrics and sequencing. Don't relitigate the decision.

**"How should we measure X / what's the North Star"** → 05. Mission and desired outcome → walk the user journey
(AAAERRR, or the phase menu: adoption, activation, engagement by business model, retention, resurrection, revenue) →
pick one focus metric plus L1/L2 inputs plus guardrails → check each against meaningful, measurable
(formula plus time window), moveable, fast feedback, interpretable, not gameable.

**"Users aren't doing Y / metric Z dropped"** → first decide: sudden change (RCA) or steady state (not an RCA) →
01 (KPI-tree the metric into a product equation) → 05 (RCA buckets, walk the funnel, cohorts to localise *where* and
*when*) → 02 (research the segment for *why*) → 03 (frame the true problem with the canvas, hypotheses).

**"How do we grow X / increase revenue"** → clarify target size, timeframe and segment → 01 (write the outcome as an
equation for the business model; pick one branch and go deep) → find the levers → 04 for loops and channels. For
non-revenue goals, find the number you monitor and decompose that.

**"Which of these should we build / roadmap"** → 03 two-level method: rank themes (product outcomes) by this cycle's
priority and allocate capacity (devs × weeks × load factor) → within a theme, product score = impact × confidence −
effort (effort from engineering) → fill capacity in order → state trade-offs and what's descoped.

**"Launch / GTM for X"** → 04 GTM section + 06 GTM template: goal (adoption vs awareness) → segment + channel +
message → pre-launch → post-launch fast follow → GTM metrics.

**"Tear down / analyse product P"** → 06 teardown method: pick a feature (not the whole company), understand company →
product → feature strategy first, then positioning → segment → flow as stages and steps → why each step exists →
metric optimised → emotions → data collected and why → experiments. Reverse-engineer what its PM was optimising for.

**"Should we use AI/LLM for this"** → 07: the intern test, data availability, failure-mode checklist, then how you'll
evaluate (offline evals plus downstream user behaviour).

**PM case interview** → identify the question type, then follow its flow below. Common to all: write the prompt down
and underline every word; clarify **Scope → Goals → Constraints** (full S-G-C for design, improvement, strategy, GTM;
scope only for guesstimates, metrics and RCA); clarify by **stating an assumption and asking if it's right**; restate
the question; **don't ask what you are meant to answer** (which segment, which features); confirm each step's
conclusion before moving on. Interviews are decided in the first 10–20 minutes (understanding the problem and user), and
evaluation is ~80% analysis, ~20% answer. **Prioritisation is the hidden test** in every type.

## PM interview question types and answer flows

| Type | Flow | Expected output |
|---|---|---|
| **Product design** ("design X for Y") | S-G-C (push market-sizing choices into clarification) → quick personal-experience pass → users wide and deep → pick a segment by size × spend × pain intensity → journey phases with **happy and unhappy flows** → prioritise pains → solutions (mostly simple, one creative) → MVP by impact × complexity, adjusted for the cost of going fast → NSM + adoption/engagement/retention + experience-specific guardrails | segment + prioritised features + MVP + metrics |
| **Product improvement** ("improve X" / "improve metric M in X") | same as design, on a product you know. Ask what the product is, its **business model**, and **which goal/metric** (outsource the choice to the interviewer). Narrow in layers (WhatsApp → consumer → groups → user-created). Pick the segment largest and most likely to move the metric; propose it with reasoning, then ask. ~95% of poor scores come from not narrowing the user and problem | narrowed user + problem + solutions + metric |
| **Metrics** ("how do you measure X / X's homepage") | narrow the product or sub-product → phase lens (what stage is the company in?) → adoption, activation, engagement (by business model), retention/churn, resurrection, referral, revenue → check in after laying out the frame. Usually a 10–15 minute add-on | metric set with formulas, read against a base |
| **RCA** ("metric dropped N% over period") | PMTSD clarifiers (product, metric formula, time and shape, segments, data) → seasonality with typical size → four buckets (data, external, internal, out-of-control; park data and out-of-control) → walk the funnel → narrow 2–3 levels before hypothesising → probe confirmed causes | root cause via dialogue |
| **Guesstimate** | clarify scope → formula confirmed (80% done) → assumptions → rounded maths → sense check. Top-down default; bottom-up, constraint-led, simple maths when they fit | a number with its formula |
| **Strategy** ("should X enter Y") | S-G-C → 5 Cs, yes/no each → majority call → where to play on the value chain → MVP → metrics → launch. No data: assume and use industry knowledge | yes/no + analysis covering every C |
| **GTM** ("launch feature/product X") | assume it's built → goal (adoption vs top-of-mind) → pre-launch (channels by budget, touch points, selective rollout, A/B or conscious bet) → post-launch (monitor, fast follow, conclude A/B) → GTM metrics → displacement risks | launch plan + metrics |
| **Technical** | mostly how APIs and data flow work (user → app → API → DB → back). API questions: use the "government-office peon" method | API/request design, data flow |

Entry-level priority: design, improvement, metrics. RCA is mostly at consumer companies. Typical loop: 1–2 product
rounds, a technical round, behavioural. Details live in 05 (metrics, RCA, guesstimates), 01 (strategy), 04 (GTM), 07
(technical) and 09 (worked answers).

## Quality bar before handing anything over

- Problem stated in one sentence as a user behaviour plus its cause, with who and why-now. A metric (conversion,
  retention) is the opportunity, not the problem. Evidence attached or flagged as assumption.
- Every research artifact states its research goal and the hypotheses it tests.
- Business outcome → product outcome link is explicit.
- At least 3 distinct options were considered. The choice criterion is visible.
- Metrics: primary, inputs, guardrails (every KPI has a KFI), each with a formula, time window and instrumentation.
- Effort estimates come from engineering; capacity uses a realistic load factor.
- Non-goals and risks written down. Open questions listed honestly.
- Readable by someone outside the team: no unexplained jargon, impact-first sentences.
