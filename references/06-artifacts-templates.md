# Artifacts and Templates

## PRD (standard template)
Header: **[Project name]** + 1-line description. Team, contributors. Status: Brainstorming / In Review / In
Development / Dogfooding / Launched. Launch date. Resources (JIRA, Figma, related PRDs).

1. **Problem definition** — 4–5 sentences a reader can react to (value, risks, alignment):
   what is the problem · who faces it · business value unlocked · how users benefit · why now.
2. **Goals** — in priority order. Measurable metrics (functional and non-functional), and why each matters.
3. **Non-goals** — explicit scope cuts.
4. **Validation of the problem** — research and data insights, user anecdotes, charts of data patterns, competitive landscape.
5. **Understanding the target audience** — segment in focus and its size, key personas, user journeys, unmet needs and pains.
6. **Solution** — overview, and how it draws on research and experiments.
   - User flows, wireframes, mockups
   - Key features (user benefits)
   - Key logic (algorithm changes, schema changes, new data types)
   - System diagram
   - Data instrumentation: events and properties per metric, in the analytics tool
   - Edge and error cases and their experience
   - Product marketing: how users will find out
7. **Launch readiness** — milestones (design done, dev done, QA, dogfooding). Launch checklist (support, ops; list
   *every* internal stakeholder and dependency, aligned early). Experimentation plan. Awareness channels:
   notifications, toasts, rich merchandising, PR.
8. **Future iterations** — next versions, parked ideas.
9. **Risks & mitigations** — why it might fail, second-order effects.
10. **Open questions & decisions taken** — what was descoped, trade-offs made (keep this log updated through reviews).
11. **Appendix** — competitive analysis, research, impact estimates, solution mind maps, alternatives considered.

**Requirement-level detail** (PRD case): list key requirements *from the customer's
perspective*, give each **acceptance criteria** (how the team knows it's done), and put a **prioritisation table** of
requirements × acceptance criteria (P0/P1/P2). Add success metrics and wireframes. Keep it to 4–6 pages with
consistent formatting. When leadership has already decided to build it (e.g. tipping because every competitor has
it), the PRD's job is to sharpen why, what exactly, done-criteria, metrics and sequencing.

**PRD additions from practice**:
- **Enumerate states**: logged in/out, empty, loading, error, corner cases. Specify captured fields and their types.
  Name the API/team you depend on.
- **Non-functional requirements with target numbers**: uptime %, latency (search in tens of ms), consistency for
  transactions, crash rate, app size. Specify **data freshness / acceptable staleness** for computed values (this drives
  caching). Derive response-time targets from user tolerance.
- **PM mocks**: include rough wireframes and a solution point of view early (mid-fi built from screenshots of the
  existing app is enough). The final version adds designer mocks, use cases, edge cases and NFRs; update it with edge
  cases before handoff.
- **Instrument impressions and events before launch**; list events + payload properties per metric.

## One-pager (pre-PRD)
Same header. Problem definition (5 questions above), goals with metrics, non-goals, validation, target audience,
solution (≥3 options considered → chosen one with criteria, user flows and wireframes, key features, key logic),
launch readiness, open questions and decisions.

## Product teardown (feature-level)
Tear down a *feature*, not a company; reverse-engineer what the PM optimised for.
1. Identify the problem or area to examine. 2. Set goals (root cause, improvement areas, behaviour insight).
3. Use it as a real user, step by step, noting where you get stuck. 4. Evaluate the journey and pain points.
5. Document and prioritise improvements (UI, performance, scalability).
Onboarding/FTUE variant: who it's for and market size; competitive differentiation; when onboarding is "complete";
metric optimised; why each design choice; data collected and why; improvements tied to the metric.

**Teardown method from the case debrief (BeReal)**:
(a) pick a product you *don't* use (you are not the target segment); (b) understand company → product → feature
strategy before the feature; (c) ask in order: positioning (ask a friend what makes it unique; positioning vs USP) →
segment, beachhead and sizing → secondary research on the "why" (acquisitions, awards) → ecosystem actors → user flow as
**stages and steps** (account → setup → value) → why each step or field exists → which metric it optimises (tie to the
core value action) → **emotions per step** → design choices explained by segment preferences → data collected and its
business use → experiments to move the metric (funnel drop-off → hypothesis → research → experiment); (d) use the
product with no inhibitions; (e) write your own questions when none are given. Start with the 5 Cs at company level.
**Learn an unfamiliar product by tracing one order ID** through every system. Teardowns become *strategy* teardowns as
you get senior: "what insight did they have that I don't?"

## Product deconstruction (company + strategy)
1. **Company info**: problem/opportunity, sector, base and primary market, metrics (ARR, DAU, time spent, ARPU, YoY/QoQ), team and leaders.
2. **Product flows**: screenshot FTUE; evolution from new to frequent user; payment flows; referral and social loops; takeaways.
3. **Purpose-led analysis** (e.g. "Hotstar 3× subscribers after ₹25 sports pack"): why is the company doing it (short- or long-term play)? Pros and cons? Tailwinds that helped? Headwinds or tailwinds if a competitor copied it? Alternatives, and why not chosen? Risks or advantages for competitors?
4. **Key proposals** summary slide.
Pain-point style (WhatsApp analysis): ask users "what annoys you?" → cluster by complaint frequency → 2×2 of
importance-to-user × importance-to-mission → per pain: quote → possible reasons (list assumptions to test) →
suggestion → priority (many complaints + quick fix = high; rare use = low; hurts other users = don't).

## Market and company analysis checklist
- **Industry**: size, growth, external factors (regulation, tech, app-store fees, licensing deals), players and their axes of differentiation (price, service, selection), JTBD substitutes (e.g. music competes with YouTube, Instagram, podcasts).
- **Competitive landscape**: known brands, value props, business models, growth tactics, how they engage audiences, review mining (Play Store, Reddit), traffic (SimilarWeb).
- **Target market**: demographics and psychographics, current problems, unmet needs.
- **Company**: revenue and cost buckets (earnings reports); growth = new customers + existing spend more; acquisition channels and why; differentiator; moat.
- **Feature competitor comparison**: user flow, number of steps, UI differences, UX differences. Look outside the industry too.
- **Why the metric matters**: list the business mechanisms (ad revenue, premium conversion, retention, data→personalisation loop, creator/supply loop), then KPI-tree it.

## Go-to-market plan (template)
1. **Goal**: adoption vs top-of-mind awareness (GTM doesn't fix retention).
2. **Segment + channel + message** (message the user benefit, not what you built).
3. **Clarifiers**: feature definition, placement decided?, adoption vs availability, budget, size of bet.
4. **Pre-launch**: channels by budget, time, audience and importance (in-app touch points, push, WhatsApp, email for
   B2B, PR, influencers, freemium); selective/invite-only/geo rollout; A/B the touch point or make a deliberate full
   launch.
5. **Post-launch**: monitor dashboards, collect feedback, **fast follow**, conclude the A/B.
6. **Metrics**: % of existing actives trying it in week 1/month 1; new users whose first action was the feature;
   cohort retention lift (via A/B).
7. **Risks**: what touch point you displace (habitual buttons lose 30–50% usage when moved); budget limits.
Details in `04-growth.md`.

## Presenting a case / capstone deck (rubric)
Judged on: (1) **communication**: simple language, jargon explained, logical slide flow; (2) **clarity and depth**:
the WHY of the problem, validation of the why, WHO faces it; (3) **creativity**: multiple *distinct* solutions, nothing
the product already has, an objective selection framework (no force-fitted scores), and a showing of how the chosen
one works (wireframes + the role of tech); (4) **data orientation**: comprehensive success metrics and impact for every
stakeholder.
Stage arc that makes a full case: market + company + metric decomposition → segment (highest impact) +
hypotheses + research (30+ survey responses, 5–6 interviews) + problem-framing canvas → 3 solutions + selection + flows
+ wireframes + metrics → PRD (system diagram, launch plan, iterations, risks, open questions).
Weekly checkpoints work as 3-slide decks: tight, one idea per slide.

**What exemplar capstone decks look like**. Nine slides: (1) context + why the metric matters to the business model;
(2) metric decomposition; (3) validation with numbers (survey 30–117 responses + 5–6 interviews + secondary data such as
SimilarWeb, store reviews); (4) persona with a verbatim quote; (5) refined problem statement + why now; (6) 2–5 distinct
solutions with an explicit scoring table; (7) annotated wireframes; (8) metrics by category with formula and rationale;
(9) pitfalls → mitigations and second-order effects. Strong touches: quantify friction against session length (a
600-character review needs ~10 min vs a 3 min 21 s average visit); a usage-gap funnel (aware 95% → read reviews 75% →
write 4%) followed by "why not / what would make you"; prototype evidence (landing-page conversion, user reactions, a
quick NLP pass over public data to prove feasibility); business-side personas (a homestay owner who depends on
reviews). Even exemplars have weak KPI formulas and unprioritised metric lists — beat them on rigour.
**PRD quality bar from reviewing a real PRD**: fill every section (system diagram, instrumentation, edge cases,
product marketing, launch, iterations, risks, non-goals) rather than leaving template text; justify any impact number
with its arithmetic; convert reviewer questions into answered decisions.

## Resume and portfolio
Treat the resume as a product: customers = referrer (wants money, credibility, to feel good; needs to discover good
profiles), recruiter (close fast; needs to cut time-to-shortlist), hiring manager (close fast and build a quality team;
needs proof of skills). Funnel: resume ~5% → screen 30% → problem-solving 50% → product sense 40% → tech 50%. Over
200 applicants in 24h, and most apply lazily, so effort alone differentiates. JDs describe an imaginary ideal, so apply anyway.
- **Resume** (provable there: results orientation, innovation, tech familiarity, stakeholder management): 1 page;
  most impactful items top-left; start every bullet with impact ("Delivered 8% sales lift by…"); **bold only skill words
  and impact**; one CTA = portfolio link (not LinkedIn); value delivered, never role description; authentic numbers
  (you'll be grilled); team impact is fine; internal tools have impact too. Bullet format "[Skill ≤6 words]: [Impact ≤50
  words]". Sections: profile, summary, experience, education (lead with it only if it's your strongest card), product
  portfolio, personal (a memorable hook).
- **Portfolio** (proves structured thinking, ramp-up readiness, curiosity, analytics): 5–10 artifacts of mixed types
  (case study, feature teardown, PRD, wireframes/prototype, SQL analysis, a built product). Play to your background
  (GitHub, Dribbble). Get reviews from working PMs and add them as testimonials. Notion first, then Framer/Bubble.
  Best of all: build a real product (a side-project site has landed people their first PM role).

## Interview prep and job search
- **Portfolio = proof**: "say wireframing → show wireframes". Recruiters search LinkedIn by keyword and credential.
- **Prep routine that works**: weekly peer mocks by question type, a topic roadmap by weakness, and revise
  the tech of your current role (the first round can be technical). Practise each question type across product types
  (marketplace, fintech, social/ads). YouTube mock channels help.
- **Expected loop**: 1–2 product rounds, a technical round, behavioural ("a time you handled conflict / a launch failed").
- **What PM interviewers screen for**: (1) communication — clear, polite, expressive; (2) ability to work with engineers
  (60–70% of the time); (3) depth in the problem space before solutions (they'll try to trap you into solutioning).
- **Getting past resume screens**: volume is the problem, not formatting. Referrals; LinkedIn Premium for 1–2 months to
  find PM managers at target companies; short **personalised** notes ("the problem I want to work on; what I bring", two
  bullets); cold email (firstname.lastname@company.com); outreach on job posts. Freshers: highlight transferable
  experience.
- **Choose company stage by temperament**, not brand or compensation. Research a company's stage via funding, customers
  and their top challenges (ask in the interview's "any questions?"). Startup prioritisation chaos is normal.
- B2B is a good first PM job to learn execution (the customer states the problem); B2C is heavier on hypotheses and
  experimentation.
- **Traits of big-tech PMs**: concise, cross-functionally literate, thorough PRDs,
  persuasive, owner mindset, networked.
- Don't over-research a company's products before an interview (little is public); focus on frameworks and mocks.
