# Discovery and User Research

Discovery = building the right product. Delivery = building the product right. Discovery is data-informed reduction
of uncertainty across Cagan's four risks: **value** (will they buy or use it), **usability** (can they figure it out),
**feasibility** (can we build it), **business viability** (does it work for legal, sales, finance, support).
Cautionary tale: a PM ships a Tier-2/3-city feature in week one without discovery, and adoption is zero.

**Generative vs evaluative**: generative research finds the *right product* (problem space; open-ended;
no product needed; most useful zero-to-one). Evaluative research checks the *product is right* (needs a product or
prototype). Tech-led products lean evaluative. **Research pains, not solutions.**

**Method quadrant: say/do × how many/why**

| | How many (quant) | Why (qual) |
|---|---|---|
| **Say** | surveys, polls, rating questions | discussion interviews, focus groups |
| **Do** | analytics/clickstream (Mixpanel, Amplitude), heat maps, session recordings (Hotjar, MS Clarity) | activity-based interviews (usability tests: give a task, observe, ask "why did you click here?") |

Quant gives direction; qual gives the why. Example: data said most learners activated their portfolio; a live task test
showed the rest couldn't tell they had already activated it (no clear CTA).

**You are not the target segment.** Treat your own reaction to a product as a hypothesis, then start from drop-off data.
**Small companies** use user calls, paid focus groups and secondary reports. **Indian users soften negative feedback**,
so probe. When you can't reach real users, recruit lookalikes via an agency with a brief. Expect to re-research when a
debrief exposes a gap. Remember **secondary actors** (a phone set up by a shop or relative; a parent paying).
**Don't trust user calls alone; verify with data** (CRED: users said a reward was too small, yet still redeemed it and
paid).

## Running discovery continuously (Höfling, Head of Product Babbel)
Teams are measured on delivery speed, so discovery gets rushed and produces polished features nobody uses. Four steps:
1. **Toolbox**: discovery has a problem space (find the opportunity) and a solution space (find the best solution). Keep a written team library of techniques (exploratory interviews, analytics, story mapping, sacrificial prototypes; Jeff Patton's Discovery Recipes, IDEO Design Kit). Revisit it in retros so you don't use one method for every question.
2. **Everyone contributes from the start**: a lead engineer or rotating engineers join interviews, ideation and prototypes, not just a late feasibility check. Invite and publicly praise their concerns (e.g. a GDPR flag). Give each person a main perspective: value (PM), usability (design), feasibility (eng), viability (business).
3. **Continuous customer contact**: at least one customer interaction per week (Torres). Automate recruiting. B2C: in-product prompt with a reward, social, support. B2B: customer success and a **lead-user pool**. Rewards needn't be cash (enterprise customers value a roadmap preview). Use self-scheduling.
4. **Ways of working**: put discovery inside delivery rituals: discovery updates in stand-up, upcoming discovery announced in sprint planning, and reviews/retros that celebrate invalidated hypotheses ("failing in discovery avoids failing in delivery"). Hold one weekly discovery decision slot. Track hypotheses and experiments on a simple Kanban discovery board.

## Hypothesis-Driven Design (Lomholt)
Assumptions → hypotheses → research → design & build. Keep assumptions **broad**, not solution-shaped ("if the wait
were shorter, people wouldn't switch coffee shops"). Narrow framing asks the wrong question: ask which ice-cream flavour
people like and nobody answers "tacos". Collect assumptions with PM, eng, stakeholders and users. Prioritise by impact on
user needs and test only what fits the time box. Keep a table: hypothesis | method (one qual + one quant if possible) |
True / Plausible / False | key finding. Validated hypotheses become user stories with success criteria.

## Finding the right problem as a new PM (opportunity analysis)
Don't inherit "the problem is X". Verify it.
1. **Know the product cold**: use it, read the help docs, learn the architecture and data flows, get walkthroughs from engineering, QA and other PMs.
2. **Quant**: categorise support tickets (CRM), the bug dump and feature requests. Add surveys, product analytics (funnels, usage) and system failure data (errors, timeouts, bad data).
3. **Qual**: talk to diverse customers. Read public reviews and social posts (Play Store, Reddit). Do competitor and trend analysis. Talk to internal customer-facing teams (sales, CS, support).
4. Combine them: quant points to *where*, qual explains *why*. Example: 30% of tickets concern attendance → users can't bulk-upload, and the page times out above 100 attendees.
5. **Opportunity table**: Feature | Issue (qual + quant) | Severity L/M/H | Compliance/legal | Impact on outcome or revenue | Competitor has it? | Usage (how many, how often) | Cost to build/fix. It folds RICE, Kano and MoSCoW into one sheet (Bucha). Tech debt counts too: if one team's deploys keep breaking other pages, splitting the monolith becomes a PM-owned problem.

## Competitive analysis (Ivtsan)
Start from the goal:
- **Sales enablement**: one-page **battle cards** per competitor (strengths, weaknesses, answers to tough questions).
- **New offering**: a feature comparison matrix. Define competitors by the job (Waze Carpool competes with public transport and walking).
- **Roadmap input**.
- **New venture**: market size and competitor business models. "We have no competition" means you don't understand the market.
Method: (1) find competitors through win/loss analysis (sales history, plus asking customers "why us / why not us"), analyst reports and conferences; (2) compare on measurable parameters customers judge you by ("4 view options vs 1", not "more flexible"), seeded from win/loss reasons; (3) package it for the audience (short for sales and execs, long for roadmap work); (4) repeat with alerts, newsletters and competitors' socials. B2C feature changes hit revenue fast; in B2B the analysis mostly arms sales.

## Jobs-to-be-Done
People "hire" products to make progress in a circumstance and "fire" them when the job isn't done. The toothbrush job
is healthy teeth, not brushing. A job is not a mission, a feature or a business objective. Pick a job that is neither
too broad nor too niche: a small group that wants it a lot beats a big group that wants it a little.
- Before writing: define the audience → market research (what they hire/fire today, hacks) → talk to users (motivation and context, barriers, current hire/fire, non-leading questions) → prioritise (importance × how badly served).
- **Template: When I… (context) / But… (barrier) / Help me… (goal) / So I… (outcome).** Solutions never appear in a JTBD.
  Discord: "When I want to jump into my favourite game, but I don't know if there are people around to play, help me safely coordinate with like-minded gamers, so I can easily enjoy my multiplayer game."
- Use it through the lifecycle: JTBD → HMW for ideation. One JTBD theme per sprint or quarter. 2–3 value props → **fake-door test** (ads or store listing) before building. GTM messaging. Post-launch PMF survey plus a "which value prop matters most" question. Revisit as you learn.
- Symptoms you need it: the team builds from its own vision (confirmation bias), gets excited by the tech challenge, or can't state the value prop the same way.

## Segmentation
Segment = shared needs + shared buying behaviour (one product and one GTM can serve them). Members talk to each other.
Dimensions: behavioural (strongest), geographic, technographic, psychographic, cultural, demographic (weak predictor).
Also free vs paid, new vs returning.
Process: state the goal of segmenting → measure engagement (time spent, journey milestones, unhappy paths) → tie to
money (purchased / not / repeat) → don't over-fragment → act per segment → validate with A/B.
**Choosing a segment**: do we understand them? Do they have willingness and ability to pay? Do we solve their pain? Are
we differentiated enough to win? Pick the segment with the **highest impact**, not the largest. Guesstimate the impact.

**Six segmentation models** (combine them in practice, e.g. "Netflix subscribers in India on Android"):
demographic; device attributes; acquisition source; product categories bought; behaviour = **RFM** (recency,
frequency, monetisation); user profile (subscriber, logged in, history).
- **Impact = segment size × likelihood of the behaviour change.** Size alone misleads (5 crore college students vs a
  ₹1 lakh course). In interviews: size × spend × intensity of the pain.
- **Actor-state 2×2**: e.g. customer × reviewer. Bought + reviews (easiest), bought + never reviews (harder), neither
  (skip), reviews but didn't buy here (a strategy grey zone: Google allows, Flipkart forbade, Amazon's middle ground is a
  "Verified Purchase" tag).
- Serve one segment well first. "If you're building for everyone you're building for no one."
- Zero-to-one needs user conversations before hypotheses (latent needs). Mature products can hypothesise from prior
  research, store reviews and forums.
- **Enterprise**: separate decision-maker, financier and end-user personas. Think consumer vs enterprise, not B2C vs B2B.
- **Segment (quant) vs persona (qual)**: one segment can hold several personas.

## Personas
One per segment: name/photo; geographic, demographic, psychographic, webographic (online tenure, device, speed);
relationship to the product; goals, needs, pains; context of use (JTBD, functional/social/emotional needs, triggers);
usage characteristics (role, environment, device limits). Gather data → synthesise → write.
Build personas **before design** and use them **during design**. They cut scope: a cooking app dropped its "survey
everyone at onboarding" idea once research showed one blended persona (tight budget + fitness), which meant only quick,
cheap recipes. Combine quant (makes the persona understandable) with qual such as interviews and shadowing (makes it
believable; people say ≠ do). Synthesise with an affinity diagram or an empathy map (think / feel / say / do). Give each
persona one summary quote that everything else stays consistent with. Fewer personas means less feature creep; with
two or more, show shared vs persona-specific features as a Venn. **Lean persona**: 80/20, mostly qual plus existing
analytics, cheap to update for fast-moving products.
Caveat (Kaba): classic personas describe *current* users, go stale, are too broad and ignore usage barriers. Keep them
dynamic and include adoption behaviour.

## Customer journey map
Timeline of actions → add thoughts and emotions → narrative. Define scope (zoom level) → pick **one** persona → outline
steps, including what happens before and after the core experience → add lanes (touchpoints/channels, emotions, JTBD,
opportunities). The journey is about experience across channels over time. A user flow is screens to a goal (see 08).

Practitioner additions (Lucidchart, Woopra): set the map's goal with cross-functional stakeholders first; source
persona data from interviews, frontline staff, support logs, call recordings, social and NPS; map **current vs future
state** and the gaps; add a **KPI and an owning team per stage** (Amazon tracks impressions → CTR → add to cart →
conversion → reviews → repeat purchase along its journey). Short B2B self-serve journeys fit in a spreadsheet; long
sales cycles need sub-stages.
**Design-thinking proof points** (IDEO): Airbnb's founders photographed New York listings themselves and revenue
doubled; Oral-B dropped a brushing-data feature because research showed data raised anxiety, and shipped easy charging
and refill ordering instead; research turned an insurer's "budgeting tool" idea into on-demand shift work (Moonrise).
Research often overturns the first idea.

## Adjacent User Theory (Bangaly Kaba — Instagram, Instacart)
- Adjacent users know the product, maybe tried it, but fail to become engaged because of barriers. The gap between
  current retention and what your PMF could support is them.
- Model user states as circles (visitor → signed up → activated → core → power/monetised). At each threshold some users
  are "in orbit". Instagram: >10 followers in the first 7 days → 65% activation. Slack: active 3 of the last 7 days is the 50/50 churn line.
- Why teams miss them: the team are power users, personas, and home-run swings.
- **Signal: cohort decay** at a state transition (e.g. free→paid falling cohort over cohort). New paid channels bring adjacent users.
- Find them: list the attributes of successful users. Each attribute is an expansion vector (urban → suburban, affluent →
  price-sensitive). Start from drop-off data, then do research.
- Build empathy: **be** them (dogfood, simulate devices and networks), **watch** them (usability tests, don't help until
  they're stuck), **talk** to them (surveys for signal, interviews for depth), **visit** them in their environment.
  Instagram logout case: users logged out because of prepaid data and shared phones, and used fake emails. The fix was
  easier re-login, not blocking logout.
- Sequencing: pick segments that differ on only 1–2 attributes. They must fit strategy. Solve in-house (already in the
  funnel) before brand-new users. B2B order: monetisable existing → indirectly valuable existing (viral) → new. Weigh
  growth trajectory, not just size. Re-evaluate quarterly, and always ask *why* an experiment won or lost.

## Choosing research methods
Axes: attitudinal (what they say) vs behavioural (what they do); qual vs quant; generative vs evaluative; context
(natural use / scripted / no product / concept).
| Stage | Methods |
|---|---|
| Early discovery | interviews, field studies, diary studies, surveys, card sorting, concept tests, focus groups (5–10 people) |
| IA / navigation | card sort (open/hybrid/closed), tree test (≤10 tasks, 15–20 min) |
| Design / prototype | usability tests (5 users per group find most issues), 5-second tests, concept tests |
| Post-launch | analytics, A/B tests, surveys, usability tests, diary studies |
For direction use a survey with 30+ responses. For depth do 5–6 interviews (3–4 per group if there are 2 groups).

## Interviews
**YC (Migicovsky) core five questions:**
1. What's the hardest part about doing [this]?
2. Tell me about the last time you encountered this problem.
3. Why was that hard?
4. What, if anything, have you done to try to solve it?
5. What don't you love about the solutions you've tried?

Craft: start wide, not with your product. Ask about real past events, never hypotheticals or the future ("Will you…?"
gets fiction). Use open prompts: "Tell me about…", "Walk me through…", "Show me how you…". Follow up and re-ask in other
words. Try the magic-wand question. Never defend or explain the product. Watch for courtesy bias. Use a semi-structured
guide and a separate note-taker. Warm up, get consent to record, close by asking for referrals. Synthesise with an
affinity diagram, then a value-proposition canvas.

**Interview checklist**: screen recruits (not friends and family; "to understand Uber drivers, talk to Uber
drivers") → derive themes from the research goal and keep a **script** → consent → warm-up → dig into **the last specific
instance** (facts, not opinions) → never lead or sell (don't name your product) → 5 minimum, ideally 8–10, each ≥30–60
minutes ("it's all about the depth"). Set the time commitment up front; give the incentive **after**, not before.
Synthesis: the **1-2-3 pattern rule** (one user = a data point, two = an anecdote, three saying the same thing = a pattern). **Unmet need = JTBD
goal + pain point.** Journey-map rows: stages, steps, thoughts/questions, actors (including secondary), emotions. A
journey map is a storytelling tool: "data often fails to communicate the frustrations."

## Surveys
Start from research questions and agree scope with stakeholders. Order questions logically. One concept per question.
No double negatives. Use balanced rating scales (very dissatisfied … very satisfied), non-overlapping ranges and a
"don't know" option. Avoid leading wording. Follow a rating with an open "Why?". Prefer "Have you ever…" over "How
likely are you to…". Don't use surveys to measure behaviour; observe it. Keep it under 10 minutes. Use screener
questions first. Pilot with a colleague, then soft-launch to a subset. Analyse by cross-tabbing segments.

**Survey checklist**: write the objective and the hypotheses first → order easy profiling → harder → end on a
lighter note → optimise for the respondent's **time** (≤2–3 minutes; pilot with 2–3 people and time it) → ask only what
you'll use (no PAN/phone/email unless needed, and last) → branch so nobody answers irrelevant questions ("shows the
person is not a good listener") → one concept at a time → show a progress bar or "8 questions, under 90 seconds".
Sample: ≥30 for projects; a clear 80/20 split on ~44 responses is enough direction, a 45/55 split is not. Worked
example (mentor-preference survey) in `09-worked-cases.md`.

## Usability tests
Use realistic, action-verb tasks ("Donate $1 to WWF via PayPal" is closed; "Donate to a charity" is open). No leading
words ("click here"). Moderated tests allow follow-ups ("Why did you do that?", "What do you understand on this
screen?"). Prioritise findings into bug / fix now / backlog using an impact-value map.
