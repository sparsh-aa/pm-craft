# Metrics, Experiments, Cohorts, Funnels, SQL

## Why metrics
They decide **what** to build (Lyft "people transported/day" → Lyft Line), **how** to build it (YouTube optimising
watch time produces addictive recs), and **how well** it works (Snap Bitmoji → stories/user/day).

## Metric hierarchy
- **North Star / focus metric**: reflects the mission and customer value, leads to revenue, measures progress. Only one. Usually tied to **active usage**, where "active" means did the key action, not logged in. Test: "If this improves, does long-term performance improve?" Top priority, not sole priority (a news site that autoplays video to boost views loses users).
- **Primary / L1**: outcome of a team or initiative. Feeds the NSM or checks its health (WAU → 7-day retention).
- **Supporting / input / L2**: leading and diagnostic, showing *where* it is failing (emails sent → opened → sellers signed up).
- **Guardrail / counter**: must not get worse (more sellers → watch purchases/user; activation ↑ but D30 retention must not drop).
Don't over-layer. Too many goals = no goals.

**Finding the North Star (Gatreddi)**: first name the game you're in: **attention** (time/engagement),
**transaction** (completed exchanges) or **productivity** (tasks done). Then test candidates. A good NSM reflects the
aha moment; expresses customer value ("orders *delivered on time*", not "orders placed"); is time-bound with a short
enough window to show growth rate; is **not driven by factors outside your control** ("5-star deliveries" depends on
restaurant food quality); and reflects a completed journey ("orders per subscriber"). The NSM is an output of input
metrics (reach/conversion × engagement per session × frequency), and inputs give individual teams ownership. Expect
iterations: LinkedIn first used endorsements, saw no business impact because recruiters distrusted them, and moved to MAU.

## Good-metric tests
1. **Meaningful**: outcome, not vanity. Quora: answer rate, not notification opens. Amazon: *high-quality* sellers, not all sellers.
2. **Measurable**: write a formula with a time window (stories/day ÷ DAU, averaged over 30 days).
3. **Moveable**: within your control (the server part of page load, not user bandwidth).
4. **Fast feedback**: Coursera uses DAU as a proxy for monthly renewal.
5. **Interpretable**: average watch time beats a weighted engagement index.
6. **Not gameable**: Wells Fargo opened 3.5M fake accounts to hit an accounts-per-customer target.

## Generating metrics: walk the journey (AAAERRR) + reach + business-specific
| Stage | Example metrics |
|---|---|
| Awareness | visits, reach, impressions, email opens |
| Acquisition | leads, qualified leads, signups, installs |
| Activation | % new users doing aha action X within Y days |
| Engagement | DAU/WAU/MAU, sessions/user, actions/active user (depth = frequency, breadth = variety) |
| Revenue | % paid, ARPU, trial→paid, cart abandonment, CTR |
| Retention | D1/D7/D30 or cadence-appropriate (TurboTax yearly, Spotify daily); churn; LTV |
| Referral | NPS, viral coefficient |
| Reach | max who could be active (subscribers, install base, 3-month actives) |
| Business-specific | "good churn" (dating), % users whose savings grow (fintech), support tickets/WAU |
Normalise engagement by actives, or user growth will mislead you. Use D7 as the leading indicator for D30/D90.
Diagnostics: new ↑ and retained ↓ = churn problem; retained ↑ and new flat = acquisition problem.
Mixpanel templates. Video subscription: focus = weekly active subscribers; activation = subscribed in 7 days ÷ new;
engagement = minutes/WAS (+ starts, completion rate); retention = 1-week WAS, same-show retention; business = ARPS.
E-commerce: focus = weekly active buyers; activation = 1st purchase in 7 days; engagement = items/WAB; retention =
1-month buyer retention + 1-week browser retention; business = average buying price (matches pricing strategy).
**HEART** (Google): Happiness (NPS, CSAT), Engagement, Adoption (feature activation, time to first use), Retention,
Task success (completion, error rate, time).

**Solution metric tree** (model answer): primary outcome (e.g. sessions/user/week, segmented by exposure vs not)
→ adoption (feature usage rate = users using ÷ eligible; interaction rate) → retention (30/90-day cohorts, exposed vs
not; churn) → feature-specific (notification CTR, trigger conversion) → sentiment (feature CSAT, NPS) → business
(premium conversion, ad impressions). For each give definition, why it matters, and how to track or a formula.

## Metric principles
- **Feature-metric method**: JTBD of the feature → the questions you need answered → map the user actions → measurable
  % metrics. Write metrics backwards from questions ("is comms creating awareness?" → sent → read → clicked).
- **Controllability**: own what your product controls. The ratings-and-reviews PM owns % of orders rated and review
  helpfulness, not orders; link to orders through a hypothesis and an A/B test.
- **Measurable, not vague**: not "user experience" but CSAT/NPS; not "engagement" but time spent or high-value
  actions; not "retention" but repeat users month on month.
- **Pair every success metric with a check/failure metric (KPI + KFI)**: urgency messaging → gross conversion, checked
  by net conversion/cancellations; referrals → new customers, checked by CAC/LTV and M0 retention of referred users
  (a ₹75 + ₹75 reward is worse than a ₹100 normal CAC). "Guardrails are usually the ones that increase your costs."
- **NSM** = the market's smallest unit of value, combining user value and business value (CRED: share of TPV). Read it
  alongside market share and profitability. **The North Star changes with the situation** (CRED: market share under
  heavy competition → profitability within ~6 months).
- **Read every metric against its own history or a larger base** (as a %). Raw counts mislead (1 lakh → 2 lakh searches
  is great on 2 lakh users, poor on 2 million).
- **Session duration** fits content products (Instagram, YouTube, Netflix), not e-commerce.
- **Attribution models** (first-touch, last-touch, multi-touch) change CAC over long cycles.

### B2C user accounting: MAU cohorts
- Split MAU (users who did the core action this month) into **M0/new** (joined this month), **M1** (second month),
  **MX/regular** (active past 60 days) and **resurrected** (returned after being churned, e.g. 2 inactive months).
- Also track **signed up, not activated** (the lowest-hanging growth fruit) and **at-risk / irregular users**
  ("MX−1"). Whether irregular users count as at-risk depends on natural category retention: high in credit-card bill
  pay (~93–94% MX retention), low in quick commerce (~50–60%, users shop around).
- **Growth identity**: new + resurrected must exceed churned each period, or the base shrinks.
- Practitioner benchmarks (one PM's experience, not universal): MX ≈ 60–70% of MAU; M1 retention ≈ 60–70%; MX
  retention ≈ 95% for very good products. **MX retention is the hardest problem**; many features exist only to lift it.
- **Retention formula**: of users active in month n, % active in n+1; exclude new users from the base; cohort-based;
  calendar month; defined on the product's core action (credit-score PM = revisits score; bill-pay PM = pays again).
  Explain dips with seasonality rather than changing the formula. **Feature-level D30** can start from first use of the
  feature (used Reorder on 1 Sept, again by 1 Oct?).
- **Physical products** (phones): MAU doesn't apply. North Star = revenue/profit and units; levers are variants and
  distribution; experience PMs watch bug reports and forums.

### Phase metric menu (answer frame for "metrics for product X")
| Phase | Metrics |
|---|---|
| Adoption | new users per month (trend); acquisition by channel (organic, referral, paid) |
| Activation | sign-up → core action within day 1 / week 1 / 30 days; "activated, not paid" (fintech); first-order offers exist to cross this step |
| Engagement | depends on the business model: fintech → **multi-product-line adoption**; ad-funded → **session days** per month and time per session; transaction apps still track sessions as a top-of-mind signal; **high-value actions** (power-user behaviours: browsing without need, multi-business use, ordering without coupons, wallet top-ups; >20–30% of monthly users doing HVAs = very strong); feature discovery (% of sessions with an impression) |
| Retention | M1 / MX retention; churn rate (e.g. no use for 2 straight months) |
| Resurrection | % and count of the churned base brought back each month |
| Referral | referred users, viral coefficient |
| Revenue (PM view) | **CAC** = (marketing + acquisition discounts) ÷ first-time users in the period (retention or resurrection discounts are *not* CAC); **ARPU** = revenue ÷ **all** active users (not just payers); AOV where usage isn't possible (e-commerce); CLTV; **payback** = CAC ÷ monthly revenue per user (₹30 ÷ ₹5 = 6 months) |
Check DAU/MAU stickiness, NPS (= % promoters 9–10 − % detractors 0–6), store ratings.
Homepages differ: in super-apps the homepage is a **kiosk** (measure % of landers who reach a product); in feeds the
homepage **is** the product (scroll and consumption). For redirect products (Google Flights), choose usage first,
then redirect conversion.

### Search metric set (MakeMyTrip case)
Usage (% of users who search vs reach PDP another way); **autosuggest CTR**; **null-search %** (meaningful null
queries are gold: map "Salman Khan jeans" → Being Human; tier-2/3 users search by celebrity); **search depth** = median
position clicked (ideal ~5–6 or lower; sponsored slots can game it, so watch downstream conversion too); search
bounce; **latency** (tens of ms; a non-functional requirement that forces caching); search-attributed conversion and
AOV vs other discovery paths.

### Non-functional metrics (put target values in the PRD)
Uptime (99.99%), consistency for transactions (a placed order must register), latency/response times, crashes and
ANRs, app size (big apps get uninstalled), page load, error rates, throughput.

## Experimentation / A/B testing
- **Run one when**: enough traffic for the MDE, the decision is reversible, the hypothesis and metric are pre-registered, and the change is isolated. **Don't** for bug fixes, obvious usability failures, tiny samples (a 6-month test is useless), foundational redesigns, or where ethics/compliance forbid it. Use a staged rollout instead.
- Steps: success + guardrail metrics → hypothesis with *because* → sample size for MDE at 95% confidence / 80% power (an underpowered "no effect" proves nothing) → feature flag, tracking exposure, primary action and guardrails → **don't peek and stop early** → check significance, guardrails and segments → document in a hypothesis log and iterate.
- Program health: velocity, win rate (20–33% is healthy; higher means too timid), time to decision, cumulative impact. Sequential/Bayesian methods allow principled early calls.
- Research makes hypotheses; A/B tests validate at scale; experimentation ties it to metrics.
- **AI features**: test the *configuration* (prompt template, model version, output format, UX wrapper), not individual outputs. Measure downstream behaviour: accepted/edited/ignored, task completion, retry rate, **D7 retention by cohort**. This is separate from offline LLM evals (output quality). Add 20–30% to sample size for output variance. Stack: prompt management → feature flag → analytics → qualitative (session replay, surveys).
- A/B tests aren't only for layouts: store screenshots (Angry Birds 2 vertical vs horizontal: +13% conversion ≈ 2.5M extra installs in launch week), labels (Ustream added "Broadcast" next to the camera icon: +12%), and **architecture changes** (new HTTP library on 10% of users for 2 weeks, then ramp up). Keep conditions fair (same time, platform, region), change few variables so results stay attributable, and use an existing tool rather than building one.
- Simple framing for any test write-up: Question → Tests → Impact. Example: Duolingo moved signup after the first lesson, ≈ +20% DAU, then copy tests added +8.2%.

**A/B checklist**:
1. Hypothesis + governance doc (historical data, research, metrics improved and hurt, mitigations).
2. Success and check metrics; expected lift via guesstimate.
3. **Sample size** with Evan Miller's calculator (baseline rate, MDE, α 5%, power 80%; lower risk tolerance such as
   payment routing → α 1%, power 95%). Duration = required sample ÷ daily eligible users. **Don't stop early.** The
   statistical test is chosen by data science/tooling.
4. Variants and weights (risky changes 1%/99%; restrict the population, e.g. India only, then randomise within).
5. Configure in the tool → QA/UAT (test users see test) → **verify events** → launch.
- **Random assignment**: hash the user ID to a stable 0–1 score and bucket it, so a user always sees the same variant.
  Avoid pre-stratification except risk-matched cases (lending).
- **Overlapping experiments**: users can land in several bad variants; mature teams use non-overlapping layers (Google's
  overlapping-experiment infrastructure).
- **Marketplaces and networks** (Tinder, Uber): network effects contaminate test vs control; use geo or time splits.
- **Risky changes** (pricing) are rarely A/B tested at big companies; test in a small country first; dogfood.
- A/B tests now mainly **measure lift attributable to your team**, not just go/no-go. Obvious features still get tested
  for side effects.
- **Instrument impressions and events before launch** (events + JSON payload → collection server → cleaning → GA/
  Mixpanel/data lake). Analytics on every screen is part of the job.
- **Rollout**: start with a **1% experiment**, then 1 → 5 → 10 → 50 → 100%, watching crash rates. Native app versions
  can't be rolled back. Big tests ~2 weeks; small startups need ~4 weeks for enough users. Plan a ramp of targets over
  months, not 100% in one shot. Measure feature adoption and repeat use, then the outcome.
- **Low-downside features**: A/B on a random ~5% slice. **Never pre-select likely adopters** (bias).
- **Analyse winners and losers** (people only dig into failures). Losers get 5–6 cuts plus a bias check; winners move to
  scaling questions.
- **Kill vs delay**: a 2-day build with bad metrics → kill; a 6-month build → diagnose and delay.
- **Behaviour beats stated sentiment**: CRED users complained the cashback was too small yet still redeemed and paid.
  Retention/churn is the only honest measure where NPS isn't possible.

## Cohort analysis
Averages lie. A cohort = users sharing a start point or trait, followed over time.
- Table: rows = cohorts, columns = time since start, cells = % returning. Read **across** (healthy curves flatten to a plateau), **down** (did newer cohorts improve?), **diagonals** (calendar effects). Day-X retention = returned on day X ÷ cohort size.
- Types: **acquisition** (*when* churn happens; Day 0→1 is usually the cliff), **behavioural** (*why*; most actionable: transactors D1 43% vs cart abandoners D1 4%), time/campaign (promo opportunists?), segment (device, tier, geo), size (beta 40% D7 vs public 12%: does it scale?).
- Variants: specific-day vs unbounded retention, return frequency, churn table, latency (time to 2nd action).
- Starter analysis: users who did the activation step within 7 days vs everyone else → compare retention. Feature adopters vs non-adopters: high adoption + low retention means discoverable but not valuable.
- Judge acquisition channels by cohort *quality*, not signup volume.
- Pitfalls: vague cohort definitions, small cohorts, comparing immature cohorts, seasonality, correlation ≠ causation (confirm with an experiment).
- Investors ask for "3-month retention" because a great download month can hide weak cohorts.

## Funnel analysis
- Define the conversions that matter → map touchpoints (journeys aren't linear) → build the funnel → segment and compare (channel, new vs returning, age, geo) → track monthly.
- Strict funnels (exact path, e.g. checkout) vs loose (ordered steps, other actions allowed). Set conversion windows from historical timings.
- Localise big drops with partial funnels (visit → search → click result → add to cart). Compare **absolute** and **relative** (step-to-step) conversion by segment to find the segment-specific leak.
- Fix: walk it yourself, remove distractions, ask what non-converters do instead, look for unexpected bottlenecks (shipping-info drop = bug), time-to-step, segments (old app version crashing).
- **Four errors**: (1) always attack the biggest drop. Instead fix bottom-of-funnel conversion and retention before pouring in more users; small frictions are often easier. (2) A high drop means bad UX. Maybe you're acquiring the wrong users. (3) The funnel ends at conversion. Post-conversion retention matters. (4) One path for all. Consider flipping the funnel.
- Channels: judge by paying customers, not new users.

## Guesstimates
Process: **clarify scope → write the formula and confirm it ("80% of the evaluation is done") → state assumptions →
round aggressively → sense-check** via another route. Ballpark = the same order of magnitude. 10–25 minutes max.
Frameworks:
1. **Top-down** (default): population → urban/rural (~30/70) → households of 4 → income bands → penetration/usage.
2. **Bottom-up**: start from one unit (your household, 10 friends) and extrapolate.
3. **Constraint-led** when there's a physical cap: McDonald's orders = tables × orders per table per ~30–40 min × hours;
   airport passengers = runways × movements/hour × seats.
4. **Simple maths** (volume/fit): tennis balls in a 747.
- **Market share is on orders, not users**: compute orders (people × frequency) before applying share. With 2–4
  players, assume an equal split unless clearly skewed. Segment by usage habit, not income.
- Reference numbers he uses: India ~1.4B; age 0–15 = 30%, 15–60 = 60%, 60+ = 10%; household = 4. (He was unsure of
  smartphone penetration — verify.)
- **Real use: feature sizing** (Swiggy Reorder: daily users → transactors → repeat orderers → impacted orders).
- Interviewers grade structure, not arithmetic. Present top-down and bottom-up; numbers optional.

## Root cause analysis (RCA)
- **Anatomy**: metric + change + period. If any part is vague, clarify ("comments" per day, per video?). **Sudden**
  drop → something recent (release, bug, external event); **gradual** decline → not a single launch.
- **Clarify with PMTSD**: product, metric formula/definition, time window and shape, segments, data/tracking issues.
- **Narrow** by platform, geography, tier, plan, category. **Seasonality, asked properly**: did we see a dip at the same
  time last week/month/year, and **what's the typical size?** (if seasonality explains 2% of a 5% drop, 3% remains).
- **Four-bucket issue tree**:
  1. *Data*: logging/pipeline failures, stale dashboards, **metric definition changes**. Mention and park.
  2. *External (influenceable)*: competitor or campaign, market trends, seasonality, **user-mix change** (a flood of
     tier-3 users lifts UPI, lowers flights).
  3. *Internal*: releases of any size, pricing changes, **A/B tests on part of the base**, **cannibalisation** (CRED
     moved Store under "More": landings −10–20%, a deliberate trade-off).
  4. *Out of control*: regulation (NPCI/RBI circulars), disasters. Park data and out-of-control first.
- **Walk the funnel**: drop present from app open onwards → likely external; drop isolated at one step → internal at
  that step (Maps API failing, a redesign hiding a field, surge changes, a discontinued category).
- **A/B ratio rule** for a falling ratio (orders ÷ visits): numerator fell, denominator rose, or both moved unequally
  (both rising with B faster = lower-intent traffic). Ask which; it halves the search.
- **L0–L3 breakdown**: L0 = NSM; **L1 = new + repeat + resurrected** (maps to owners faster than power/casual); L2 =
  visitors × conversion; L3 = by platform and source, conversion by funnel step.
- **Attribute the whole drop** (~95%) before naming a cause; account for every branch's movement.
- Narrow 2–3 levels before hypothesising. Probe confirmed causes ("yes, we changed pricing" — what and why?). Interview
  answers skew internal. If stuck, ask "is there an area I'm missing?". Positive spikes get RCA too.
- **Real life**: ~70% of root causes are tech/release-related; weekly metric reviews surface drops; analytics runs
  correlations; support tickets are the early-warning channel; slow-burn external issues (regulation) are found late;
  outages make the PM a communicator in a war room.
- A vague "improve quality of service" is not RCA: decompose QoS into components (uptime, latency…).

## Funnel decomposition (Flipkart PWA case)
Conversion = product of telescoping step fractions (orders/confirmation × confirmation/payments × … × search/home).
If conversion differs, one or more fractions must differ. Plot a **stage-gap waterfall** (mobile vs app) to find the
biggest contributor → zoom into that step → into its failure flows → segment the droppers (IP → city; device ID →
new vs returning). Data says *where*; research says *why*.

## SQL a PM should be fluent in
Logical order: **FROM/JOIN → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT**. So aggregate filters go in
HAVING, and SELECT aliases don't exist in WHERE.
Core: SELECT, WHERE (comparison, IN, BETWEEN, LIKE, AND/OR/NOT, IS NULL — never `= NULL`), GROUP BY with
COUNT/SUM/AVG/MIN/MAX, HAVING, ORDER BY, LIMIT/OFFSET, JOINs (INNER, LEFT, RIGHT, FULL on keys), set ops (UNION vs
UNION ALL, INTERSECT, EXCEPT). Keys: primary key = unique row id; foreign key = a reference to another table's PK.
Data types vary by engine, so check the docs.
```sql
-- customers with more than 2 orders since 2022
SELECT customer_name, COUNT(order_id) AS num_orders
FROM orders
WHERE order_date >= '2022-01-01'
GROUP BY customer_name
HAVING COUNT(order_id) > 2
ORDER BY num_orders DESC;
```

**Why PMs self-serve basic SQL**: faster first-round analysis without waiting for analysts. Production data is often
access-restricted and queried via internal tools; dialects vary (KQL at Microsoft). Interview SQL follows the same
ladder: SELECT/WHERE → aggregation (GROUP BY/HAVING/ORDER BY/LIMIT) → joins. Structured (tables) vs unstructured (JSON,
NoSQL) is worth one sentence. Practice templates: host ratings, peak-month bookings on an Airbnb-style schema.
