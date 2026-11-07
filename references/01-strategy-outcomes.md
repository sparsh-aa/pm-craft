# Strategy, Outcomes, KPI Trees, Systems Thinking

## Vision and strategy as guard-rails
The problem space is infinite. Vision and strategy decide which customer problems are *ours*. Swiggy shouldn't build
flight booking even if its users need cheap travel. Airbnb shouldn't tackle education. Products exist to generate
business benefit. Know the true WHY before any research or build.

Product development life cycle: plan & discover → build → launch → measure → learn → iterate.
Discovery steps: (1) understand business vision and strategy, (2) product vision (why), (3) initial product strategy
(market and needs, key features, business goals), (4) prototype (de-risk feasibility, then value and usability),
(5) test & learn, (6) **iterate, pivot or kill** (repeated pivots mean kill).
How much discovery depends on stage: a new market needs heavy discovery. Churn on a mature product needs lighter,
usability-focused discovery.

**Company → product → feature strategy**: the problems you pick must align with product strategy,
which must align with company strategy. Strategy = goals + the choices made to hit them. Flipkart 2016: company
strategy = grow in tier-2/3 cities → research insight = new users can't relate to an English-only site → product
strategy = local languages → feature strategies = search understands local scripts and transliteration; reviews accept
local languages. Second-order work follows: every system must handle new scripts, and moderation must catch abuse in
Marathi. No company strategy means no product or feature strategy.

**Three kinds of PM thinker**: *technology thinkers* ("it can be built, let's build it"; common for ex-engineers),
*problem thinkers* (spot a problem, immediately build a feature), *outcome thinkers* (define the end state, work
backwards). Roadmap test: Team A = "build features 1, 2, 3" (output); Team B = "to move metric A, pursue opportunity X"
(outcome); real life is often Team C = "to move metric A, build feature X". Team C skips the opportunity layer because
nobody mapped the business objective to product objectives.

**Timing / why now**: the same idea fails or wins on timing (fantasy sports before and after cheap data; quick
commerce tried in 2017 vs after 2020). Always ask why now.

**How metric focus cascades in practice (CRED)**: each quarter or half the company picks a focus (growth vs
profitability) → teams pick a product focus → a PM owns 1–2 small metrics. Example chain: company goal = growth and
retention → engagement feature "card summary" → needs each card's variant (HDFC Regalia vs Diners Black) → PM metric
= % of cards with a variant name attached. The North Star itself can change: CRED moved from market share (heavy
competition) to profitability within ~6 months.

## Business basics every PM should be able to say
- **P&L ladder**: revenue (top line) − COGS = gross margin; − R&D, sales and marketing, support, G&A = operating profit;
  − interest, taxes, depreciation = net profit (bottom line). Growth means the top line **and** the bottom line grow.
  Similar revenue but higher profitability gets a higher valuation (Zomato vs Swiggy at IPO).
- **All business outcomes are lagging**: they are reported after money hits the account.
- **Revenue equation per business model** (every figure is per period):

| Model | Revenue equation | Examples |
|---|---|---|
| Sell product/service | units × average price (or customers × AOV) | iPhone, a course |
| Rent | rental customers × avg rental value per unit × avg rental duration | Zoomcar, Furlenco |
| Commission | commission rate × transactions (or × total sales value) | Flipkart, Uber, Airbnb (commission, not rent: it owns nothing) |
| Subscription | subscribers × average fee | Netflix, Prime |
| Usage | users × avg usage per user × price per unit | AWS, LLM tokens, electricity |
| Advertising | impressions × CPM, clicks × CPC, or actions × CPA | Google, Meta, YouTube |

- **Companies stack models as they grow** (Amazon: books → marketplace → Prime → AWS → ads; LinkedIn: Premium +
  Talent Solutions + ads). Adding a business model is a growth lever. No model is "better": ads need a huge user base
  first; usage pricing only works if users get more value by using more.
- **Value delivery before value capture**: leakage (ad blockers, modded apps) only matters after core value is proven.

## Business outcome vs product outcome
| Business outcomes (lagging, company performance) | Product outcomes (leading, human behaviour, team can move) |
|---|---|
| grow revenue, profit, margin, market share; reduce opex | search CTR, funnel conversion, time spent/user, repeat rate, activation % |

Translate every lagging outcome into the behaviour change it depends on. Revenue grows if customers:
- **buy sooner** (reminders, urgency, "only 10 left"),
- **buy more** (cross-sell, bundles, more seats or months),
- **pay more for the same** (subscription, renewal discount, premium tier).
Without a product strategy, discovery still finds wins, but the product turns into "feature soup".

## KPI tree: map business outcome to product outcomes
Root = business outcome or North Star. Leaves = product outcomes a team can own. Write the root as an equation and
keep decomposing.
- Revenue = transactions × AOV = (customers × txns/customer) × AOV; customers = new + repeat; new = new users × conversion.
- MAU = new + returning + reactivated; new users = leads × conversion; leads = paid + organic.
- Time spent listening = users × session frequency × % sessions with listening × avg session duration × % session time listening.
- Completed trips = trip requests × fulfilment, capped by capacity = active drivers × hours/driver.

Two ways to grow a branch:
- **Mathematical** (solid line), from equations: funnels, segments that sum to a whole, business-case formulas.
- **Hypothesis** (dotted line), from research: interviews, journey maps, aha-moment analysis. Validate or replace these over time.

**How to build one (Leyrikh, TransferWise)**: (1) brainstorm every area of impact with its metric (transactions, avg
volume, conversion, contact rate, cancellations, fraud, churn, LTV); (2) connect upward by asking **"Why?"** until you hit
the core goal (contact rate ↓ → support cost ↓ → transaction cost ↓ → margin ↑ → growth); (3) fill gaps downward by
asking **"How?"**: split by process (hear → land → register → first purchase) or by segment (UK + US + …); (4) remove
overlaps. Drop composite metrics like NPS or LTV, because other branches already drive them. Several valid trees
exist for one product; pick the split that matches how the team is organised.
**Using it to prioritise**: to compare two projects on different branches ("+0.5% conversion vs −10% contact rate"),
walk both up to their first common parent metric and compare their impact there using the math links. Leaves are where
project ideas go. Branches are how you divide ownership between sub-teams without overlap. The math links give you a
spreadsheet growth model.

Rules: MECE branches (no overlap, no gaps). Arrows point up ("contributes to"). Colour metrics by data trust
(self-serve / verified-not-self-serve / untracked / unreliable). Thicken edges by strength or mark "next to work on".
Build it with marketing, BI and sales, and share early drafts. Don't detail branches that aren't in focus. Review
quarterly and whenever strategy or learning changes. Replace "track everything" dashboards with the tree.
A KPI tree is not a forecasting tool. It clarifies outcomes and levers.

### KPI-tree construction rules (from case debriefs)
- **Clarify first**: target size, timeframe, segment/region. Jumping to solutions on "increase YouTube revenue" is a red
  flag. For non-revenue goals ("no regulatory issues" is not a metric), find the number you monitor (complaints) and
  write *it* as an equation.
- **Actor/action rule**: a node about users becomes a % (share of users who do X); a node about actions becomes an
  average (actions per user). Keep per-user terms explicit.
- **Balance units** on both sides of every equation (ad impressions = impressions per minute × minutes).
- **Multiplicative before additive**: decompose ratios multiplicatively first; additive splits (new + repeat,
  segment A + B) belong near the leaves. Breaking down ≠ slicing by segment.
- **One step at a time**, no circular nodes, mutually exclusive branches, measurable units (streams, sessions, plays).
- **Constraints are fixed nodes**, not levers: ad impressions per minute (set to protect UX), agent work hours.
- **Stop decomposing** when a node is measurable, actionable and specific.
- **Scope before you build** so you don't mix branches (pre-order vs post-order support; DAU ≠ daily active customers).
- Product outcomes can decompose into further product outcomes, but name the business outcome first.
- **In interviews with many revenue streams**, pick one branch and go deep. Showing structure once is enough.
- **Why product outcomes lead**: they measure the behaviour change that the business result depends on. "Only when a
  user clicks the button can you record a conversion."

### Worked tree: YouTube ad revenue (canonical example)
Assume impression-based, skippable ads on every video.
```
Revenue            = ad impressions × cost per impression      (rate card, ~constant)
Ad impressions     = video plays × avg ad impressions per play
Ad imps per play   = ad impressions per minute (CONSTRAINT) × avg play duration
Avg play duration  = video length × avg completion rate
Video plays        = video viewers × avg plays per viewer
Video viewers      = visitors × (1 − bounce rate) × thumbnail CTR
```
Real features map onto the levers: recommendations → plays per viewer ↑ and bounce ↓; hover preview → thumbnail CTR ↑;
playback speed, chapters and the "most replayed" graph → completion ↑ (and more mid-rolls served). Once the tree is
drawn, the answer to "increase YouTube revenue" is obvious.

### Worked tree: Swiggy support load (case debrief)
Agents needed = agent-handled queries ÷ (work hours ÷ avg handling time); queries = orders × % orders with issues.
The two product outcomes (roadmap themes) are **↓ % orders with issues** and **↓ average handling time**. See case 4 in
`09-worked-cases.md`.

### From outcome to opportunity (the chain)
Business outcome → granular product outcomes → actor + segment (sized) → **opportunity = lever move × baseline** (e.g.
Prime subscribers who review 5% → 6% on a ~75M reviews/yr baseline ≈ +15M reviews) → behaviour change needed → "How might we…" statements → solution
hypotheses → validation. Amazon reviews worked example in `09-worked-cases.md`.

## Opportunity Solution Tree (Torres) and continuous discovery
Outcome → opportunities (customer problems/needs) → solutions → experiments. Always start from the outcome, not the
solution. Opportunities sharpen as research deepens. Pool example: "maintain a filter-check list" becomes "manual
filter monitoring", which leads to a better solution (remote pressure sensing + alert). Discovery has two
dimensions: opportunities and solutions.

## Impact Mapping (5 levels) — stops jumping from goal to feature
1. **WHY** — impact metric for a strategic priority.
2. **WHO** — actors whose problem blocks it. Include second-degree actors (family, admins, read-only users, internal
   staff) and adjacent users.
3. **HOW** — behaviour change needed ("an outcome is a change in human behaviour that creates value", Seiden). This
   comes from research, not invention. Phrase it as **"How might we [intent] [actor] [outcome]?"**. If you can't, you've
   slipped into features.
4. **WHAT** — candidate solutions (least important level). Being on the map is not a commitment.
5. **WHETHER** — experiments that validate them, with explicit assumptions and recorded results.

## OKRs without theater
Signs of theater: an arbitrary count of OKRs; silo teams sharing OKRs they can't move alone; key results that are
impacts (lagging). Fixes: state your own reason for using OKRs. Don't turn 100% of work into OKRs: KRs are proactive
strategic bets, KPIs are evergreen health metrics. Use **leading indicators reverse-engineered from the proven customer
journey**, i.e. the common behaviours of your last N buyers or upgraders.

## Systems thinking
- System = components + interactions + environment + functions + objective. Products are designed systems inside
  emergent ones (a job app touches the labour market, GDP and policy). Optimising one metric is linear thinking. Ask
  about 2nd- and 3rd-order effects.
- **Bottlenecks**: fix the constraint itself. More inflow just grows the jam. Example: Facebook's "7 friends in 10 days"
  onboarding fix beat buying more signups. After the fix, ask where the next bottleneck appears.
- **Feedback loops**: reinforcing loops (often runaway) and balancing loops. They exist inside the product
  (recommendations) and outside it (Instagram → gym and travel behaviour).
- **Iceberg**: events (a bug, a queue) → patterns (all bugs in one feature) → structures (who built it, staffing).
  Act at the structure level.
- Solve at a different level than the problem. Example: a charity can build a shared volunteering platform instead of
  its own recruiting tool.
- **Canonical second-order example (Zomato address change)**: a "customer-delight" feature lets users change the
  address after ordering → the rider already en route is redirected → longer delivery → less rider capacity in that
  area → other orders delayed → support calls and cancellations. Zomato's real rule: changes only in the first 60
  seconds, then via support. **List every actor before shipping.**
- **Three tools**: (1) *behaviour-over-time graphs* (look at a metric over a window and let questions surface);
  (2) *iceberg* (keep asking why; include "tracking changed in a release" as a possible cause); (3) *causal diagrams*
  with reinforcing loops (more leads to more) and balancing loops (Sacks' Uber napkin: demand → drivers → density →
  faster pickups → demand).
- **Learn an unfamiliar product by tracing one order ID** through every system it touches. That maps the stack.
- **Rules and constraints prevent chaos**: return windows, masked phone numbers, address-change windows. Ask "how might
  this product fail?" and **measure every rule** (e.g. how many users hit a referral cap, and how many of those are fraud).

### Analyse the business first: the 5 Cs
Start with customers. The Cs are slices of one pie, not a priority order.

| C | What it tells you | Interview sub-checks |
|---|---|---|
| **Customers** | how big the market is | needs and unmet needs; switching cost; buying power (watches premiumise, OTT can't); journey synergy with our product (Google → shopping starts with search) |
| **Competitors** | what share we can realistically get | number of players (consolidated 2–3 players with ≥40% each = high barrier; fragmented = easy entry but must differentiate); business models and cost structure (is anyone profitable?); what only we can offer. Ask *why and when* customers choose them, not market-share tables |
| **Climate** | how risky the model is | regulation and economy (28% GST on online gaming; RBI pauses; demonetisation helped PhonePe). Fintech is far more exposed |
| **Company** | how well suited we are to execute | strengths/weaknesses (SWOT); mission fit; synergy with the core business; reuse brand or launch a new one (Zomato vs Blinkit); the annual leadership direction (don't pitch cost-raising features before an IPO) |
| **Collaborators** | who amplifies or blocks us | partner or acquire; app stores' 30% cut; payment-gateway fees; OS "digital wellbeing" silencing notifications; non-tech actors (traffic police, unions); exclusive supplier deals |

- **No competitor usually means the wrong market** (too small, unprofitable) unless it is genuine category creation.
  Find people who tried and failed.
- **Strategy is a set of choices**: "10x better on one thing" vs "5x better on one and at par on the rest".
- **Strategy interview flow** ("Should Amazon enter quick commerce?"): clarify (S-G-C) → 5 Cs, mark each yes/no → the
  majority decides → **where to play on the value chain** (Facebook → travel: fits *discovery*, possibly booking via
  partners, not transport or stay) → MVP features → metrics → launch plan. Interviewers have no market data: make
  assumptions and use industry knowledge. The question tests structure, not accuracy.
- **Moats for low-differentiation products**: brand and trust (CRED after BBPS opened bill fetch to everyone),
  distribution, reliability and ease (GPay), rewards. Against marketplace leakage, give value only the platform provides
  (training, dispute handling, payout control, safety features).

### Analyse the product: model, actors, flows, loops, infrastructure, rules
- **Business model(s)** (table above).
- **Actors**: internal (design, engineering, analytics, leadership; they can change direction) and external (every
  side: consumers, restaurants, riders; merchants small and big). Regulators belong to Climate. The common trap is
  thinking only about the end consumer ("fewer cancellations" — drivers ask "what about us?").
- **Flows**: information (every product; search and APIs), material (physical goods only), cash (transactional;
  may sit on another actor's side, e.g. advertisers). Flows can be two-way (returns).
- **Feedback loops** (become growth loops), **infrastructure** (catalogue, search, checkout, payments, OMS), and
  **rules and constraints** (above).
- A PM usually owns one component (notifications, referrals, ratings, pricing, support) inside this whole.
- **Regulation as an out-of-control driver**: fintech circulars (NPCI/RBI) can force changes in short compliance windows.
  **Cannibalisation** can be a deliberate trade-off.

## What separates top-1% PMs (McAllister) — use as a self-check
Think big (hunt elephants). Communicate a case that can't be refuted. Simplify (80/20, stop over-building).
Prioritise: sequence quick wins vs platform bets, offence vs defence (ops, tech debt, bugs). Forecast and measure:
estimate benefit from comparables, measure after launch, metrics are P0. Execute through the last mile. Understand
technical trade-offs and great-vs-good design. Write effective copy. Earn trust (know each stakeholder's third rails).
Dig for data yourself. Push back and win. Adapt to change without drama. Be driven by impact, not promotion.
