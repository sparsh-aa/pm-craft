# Worked Cases

Use these to calibrate the depth and shape of a good answer.

**Provenance.** Cases 1–6 follow model answers and case debriefs; case 3's answer is the prioritisation *method* (see
`03-problem-framing-ideation.md`). Case 7 is a worked solution. Cases 8 onward come from lectures and interview prep.

## 1. Spotify India: "increase time spent listening" (a four-stage case project)
**Why the metric matters to the business**: more ad inventory (free tier), higher premium conversion, better retention,
a data → personalisation → retention loop, and a creator/exclusives loop (engagement attracts supply, which attracts users).
**KPI tree**: Time spent listening = users × session frequency × % sessions with listening × avg session duration × %
session time spent listening.
- Session duration ← content relevance, listening flow (seamless transitions), in-app engagement (playlists, lyrics).
- Session frequency ← content freshness, personalised triggers (notifications, streaks, Wrapped), habit formation.
**Segment and problem** (M2): pick the highest-impact segment, e.g. infrequent users who use Spotify only for isolated
events (road trips, studying) and not daily routines (commute, workout). Hypotheses → survey (30+) + 5–6 interviews →
problem-framing canvas.
**Root causes** (mind map): no contextual prompts; competitors own routine moments (YouTube at the gym, FM in the car);
content–context mismatch; "commitment" perception; no daily triggers or integrations.
**Three distinct solutions**: (a) ML activity-based recommendations (sensors, calendar, weather); (b) integrations with
daily tools and devices (calendar, Strava, car Bluetooth auto-play, smart-speaker routines); (c) gamified habit loop
(streaks, context milestones, rewards).
**Scoring** (1–3 on value, usability, feasibility, viability, scalability risk + likelihood of success): integrations
16/18 > activity recs 15 (feasibility 1, not enough data to personalise) > gamification 14 (appeals to a niche; risk of over-gamifying).
**Metrics**: session frequency/user/week (primary; exposed vs not exposed) → integration usage rate, playlist
interaction rate → 30/90-day cohort retention and churn vs unexposed → notification CTR, smart-speaker activations,
calendar-trigger conversion → feature CSAT, NPS → premium conversion, ad impressions.
**Launch**: awareness via notifications, toasts, rich merchandising, PR; partner dependencies aligned early. Open
questions and second-order effects listed.
Average-time variant: average = total ÷ count, so decompose the fraction first (avg listening time per user
= total listening time ÷ listening users), then split the numerator by category. Splitting by genre is *slicing*, not
decomposing.

## 2. GameOn: redesign the referral program — debrief
Data: 20M registered, 1.5M DAU, 45 min/day, D30 retention 35%, paid CAC $2.50, ARPU $0.50, referral conversion 2.4%,
participation 12%, K = 1.1, weak virtual-currency reward, poor tracking.
**Define success first**: a referred user who plays ≥1 game. Business outcome: lower CAC through organic acquisition.
**Tree** (walk the real journey: tap Refer → share sheet → send → click → store → install → register → first game):
successful referrals = referrers × avg invites per referrer × visits per invite × downloads per visit × first plays per
download. Each factor is a product outcome.
**What influences each node**: who *can* refer (anyone vs "played ≥5 games"); the incentive; the share copy ("can you beat
my score?" challenges get clicks); the store page (usually 15–30% conversion: screenshots, size, reviews); the first-game
value prop ("start your streak", free gems).
**The missed lever: referral cycle time** (share → referee's first game). Virality is speed, not just count; link expiry
compresses decisions. Growth is always tied to a timeline.
**Holistic habits**: pair the KPI with a KFI (don't worsen CAC/LTV; FrontRow died with CAC > LTV); pre-mortem (fraud and
gaming: "incentives always drive the wrong side of some humans"); serve both actors; understand why people share
(validation, identity, achievement; NFX "Why People Share"); design game dynamics before mechanics. Incentives buy
adoption, not habit. First referral launches often fail.
Earlier worked ideas still valid: ask in context (after a win), tiered/asymmetric rewards, reward on the referee's
engagement, channel attribution, challenge-a-friend multiplayer. Check payback against the $2.50 paid CAC and test
cannibalisation with an on/off test.

## 3. Edtech platform: 3-month roadmap with 2 engineers — method
Groups sequenced by event order or user journey, or used MoSCoW without a way to compare impact. **The right answer is
the method, not a list**: rank **themes** (product outcomes) by this quarter's company priority → allocate engineering
capacity by % → capacity = devs × weeks × **load factor** (30–50%) → within a theme, **product score = impact ×
confidence − effort** (engineering-estimated effort, KPI-tree impact, confidence by process stage) → fill capacity in
order, spill the rest. Full method in `03-problem-framing-ideation.md`.
Earlier worked mix (for the specific sheet): cheap high-leverage growth (referral leaderboard 1w, international payments
2w, mock-interview scheduling 2w), enabling work for the new vertical (coding playground 6w), and reliability debt that
cuts on-calls (logs/health 2w, CI/CD 3w). Defer big platform bets (live platform 12w, cohort builder 10w). State what's
cut and why. With 2 engineers × 13 weeks × ~50% load factor, there are only ~13 usable dev-weeks.

## 4. Swiggy: rising customer-support queries — debrief
**Not an RCA**: nothing suddenly changed. The goal is profitability before IPO, and support is a cost centre.
**Clarify Scope → Goals → Constraints**: which vertical (food vs Instamart vs Genie), which channel (phone vs chat; an
agent handles one call but several chats), which actor (consumers, restaurants, delivery partners), pre- vs post-order.
Silent assumptions here are "a no-hire call".
**Tree** (phone, food, consumers, post-order):
```
Agents required      = queries reaching agents ÷ queries handled per agent
Queries (post-order) = orders × % orders with issues
Queries per agent    = work hours (CONSTRAINT) ÷ avg handling time
```
Orders can't go down; work hours are fixed. So there are exactly **two product outcomes / roadmap themes: ↓ % orders
with issues and ↓ average handling time.**
- Theme 1: break issues down by type (order status, payment, delivery, items, packaging). **Dependency trap**: if payment
  issues drive queries, the payments PM owns the fix and their quarter is sealed — stakeholder management is the job.
  Packaging issues at one restaurant go through its key account manager. Existing ideas fit here: proactive tracking and
  ETA accuracy to cut WISMO, auto-refunds for missing items.
- Theme 2: IVR language routing (language mismatch inflates handling time); chat-first support deflects WISMO before a
  call. Guardrails: CSAT, refund cost.
**Estimate**: present top-down (cities × internet × % ordering online × share × frequency) and bottom-up (visits ×
conversion, with internal data). Interviewers grade the structure; "95% will not even ask you to calculate." Define
terms: daily active users (app opens) ≠ daily active customers (orderers). Segment by habit, not income.

## 5. BeReal: onboarding/FTUE teardown — debrief
- **Segment**: Gen Alpha / young Gen Z tired of filtered social media and of platforms their parents use (the insight
  behind the name). They're leaving *aspects* of social media, not social media.
- **Positioning test**: ask a friend what makes it unique; clustered answers (authentic, real-time, no filters) mean it
  worked. Positioning ≠ USP.
- **Why it matters**: Apple App of the Year 2022; acquired by Voodoo (a casual-gaming company) for ~€500M. Ask *why a
  gaming company*: same young audience, and gaming companies spend heavily on user acquisition and ads.
- **Flow as stages**: account creation (name, username, DOB, location) → setup (find friends, contacts) → value (first post).
- **Onboarding metric**: **% of first-time users who post their first BeReal**, because posting is the core
  value. (Not "first post + N friends".) Drop jargon like "activation" and say what you want onboarding to achieve.
- **Data and its business use**: DOB → **age targeting** for advertisers; App Tracking Transparency prompt →
  an ads model; the key insight is the **photo's EXIF geotag** within the 2-minute window BeReal chose, giving
  hyperlocal, daily-precise location of every active user (more precise than city/PIN/IP). Plus "every user is a
  creator" (100% of actives post daily vs ~1% creators elsewhere).
- **Emotions**: the 2-minute notification creates anxiety. Dual camera is the surprise/aha moment. Dark, minimal design
  matches Gen Z/Alpha preferences.
- **Experiments**: treat onboarding as a funnel → find the biggest drop (contact sync, first selfie) → hypothesis →
  research → experiment (hand-pick a small circle instead of syncing all contacts; an introductory selfie to initial
  contacts; a different flow for older users by DOB). You are not the target segment: start from drop-off data.

## 6. Amazon review-request email funnel by segment (exercise)
Overall: sent 10,000 → read 500 (5%) → star rating 225 (45% of readers) → text review 56 (25%) → submitted 45 (80%).
Gold 20–30y vs Bronze 50+: read ≈5% both, rating ≈43–46% both, **text-review step 25% vs 13%**, so the writing step is
the segment-specific leak for older users. Ideas: voice reviews, prompts or templates, rating-only submission.
Lesson: compare **relative (step-to-step)** conversion by segment, not only absolute counts.

## 7. Tipping at a hyperlocal delivery app (PRD exercise)
Leadership has decided to ship tipping by end of January (competitor parity). PRD focus: why it matters (delivery
partner earnings and retention, so better service), customer-side requirements (when to prompt: pre-order vs
post-delivery; preset amounts; custom amount; edit/skip; clear disclosure that 100% goes to the partner), acceptance
criteria per requirement, success metrics (tip attach rate, avg tip, partner retention, no drop in order conversion
or rating), wireframes, and a prioritised requirements table.

## 8. Amazon: "increase the number of reviews"
- **Clarify S-G-C**: text vs video vs ratings; which Amazon (e-commerce, Prime Video, Goodreads); global vs India; how
  big an increase (1–5% vs 50% changes the approach); constraints.
- **Business outcomes of reviews first**: conversion; trust → repeat purchases; informed buying → fewer returns and
  cancellations; more prepaid orders (lower COD cost); ranking and filter signal; seller feedback; an **SEO content
  loop** (reviews indexed by Google bring new buyers at zero CAC). Guardrail: % fake reviews.
- **Tree** (actor → %, action → average): reviews = reviewers × avg reviews per reviewer; reviewers = customers × %
  customers who review; customers = first-time + repeat; reviews per reviewer = items purchased per reviewer × % items
  reviewed (items, not orders, are the unit).
- **Segment**: customer × reviewer 2×2. "Reviews but didn't buy here" is a strategy grey zone (Google allows it,
  Flipkart forbade it, Amazon's middle ground is the Verified Purchase tag).
- **Opportunity**: Prime reviews/yr = subscribers × orders × items per order × % reviewers × % items reviewed. Moving
  reviewers 5% → 6% on a ~75M baseline ≈ +15M reviews.
- **HMW**: "How might we get first-time Prime customers to write a review?" Hypotheses (effort, forgetting, no benefit,
  privacy) → validate with research before solutions.

## 9. Flipkart mobile-web login (2016) — problem framing end to end
- Context: leadership goal = tier-2/3 growth; research showed installing the app was the friction (slow networks, 8 GB
  phones). Flipkart and Google built the world's first **PWA**.
- A year later mobile-web conversion lagged the Android app. Value: mobile web = 15% of traffic growing 50% YoY (why now);
  closing the gap ≈ **₹1,000 crore incremental annual revenue**, ~10% more new customers.
- **Localise**: telescoping funnel fractions → stage-gap waterfall → biggest gap at PDP → checkout → the login prompt →
  failure flows (bounce off login, forgot-password drop-off) → droppers were tier-2/3 (IP → city) and new (device ID).
- **Research**: 1:1 interviews + usability tests with agency-recruited lookalikes. Finding: users were **alien to email +
  password** (their internet was WhatsApp/Facebook with phone + OTP). An engineer in the debrief asked how they had set up
  Android without email → re-research → **phones were set up by a nephew or the shop** (a secondary actor).
- **Canvas**: true problem = "users can't log in with email and password because they are alien to these methods"
  (conversion is the opportunity, not the problem). One slide to CEO and CFO; a 30-minute meeting ended in 15; ≈ ₹1,000
  crore over ~1.5 years. Solution direction: phone + OTP login.

## 10. TripAdvisor date entry (2012–14)
Business model: paid per click-out to booking partners. **Data**: users who entered dates were far more likely to book
(correlation). Why not? Unsure of dates, browsing, wanting a price ballpark. Ideas: open the calendar on page load;
prefill D+2; hide prices until dates; show cheapest dates. **Hypothesis**: "Opening the calendar on page load will
increase visits with dates entered, for desktop users only, raising conversion by X%, realised N days after rollout."
Measure dates entered **and** conversion. **Shipped**: calendar on load with **colour-coded cheaper/pricier dates**;
showing exact prices *reduced* date entry (people got what they wanted). The idea came from a designer.

## 11. Edtech platform: alumni engagement
Goal: monthly active learners ↑. Segment: alumni (large and growing) over current learners. Research: no learning after
the course; want just-in-time help, aspirational people, bite-sized, **live over recorded**. Ideas at three levels:
simple (newsletters, flashcards, ask-a-mentor), stretch (alumni mentors, AI mock interviews), outrageous (lifetime
placement). Risk filter: content subscriptions fail viability; audiobook summaries fail value. Chosen: mentoring
platform → mind map (actors, benefits, do-not-wants, interactions → mentor/mentee/admin views → jobs → details) →
saga/epics/stories/tasks.

## 12. Mentor-preference survey — hypothesis-driven survey
Sent to ~100+ engaged learners, a few dozen responses. Header: "8 questions, under 90 seconds". Flow: profiling → current practice →
hypothesis question (same mentor vs different mentor each time) → mentor-choice factors → reaction → optional call (asked
last). Results: a large majority wanted different mentors (the product sold same-mentor packages); **years of experience beat
top-company brand** (hypothesis disproved, changed mentor sourcing). A clear 80/20 split on a small sample is enough direction.

## 13. YouTube revenue KPI tree — see `01-strategy-outcomes.md`
Revenue = ad impressions × cost per impression → plays × impressions per play → impressions per minute (constraint) ×
play duration → viewers × plays per viewer → visitors × (1 − bounce) × thumbnail CTR. Features map onto levers
(recommendations, hover preview, playback speed, chapters, "most replayed").

## 14. MakeMyTrip hotels
- **Search metrics**: % of users who search; autosuggest CTR; null-search % (map meaningful nulls: "Salman Khan jeans" →
  Being Human); median search depth (~5–6 ideal; watch sponsored slots); search bounce; latency (tens of ms → caching);
  search-attributed conversion and AOV.
- **RCA: monthly active customers dropped.** L0 = MAC (keep the customer unit). **L1 = new + repeat + resurrected.** L2
  (new) = new visitors × new-visitor conversion (100 × 80% → 100 × 60% is a conversion problem; 80 × 80% is traffic).
  L3 = visitors by platform and source; conversion by funnel step. Attribute ~95% of the drop before naming a cause.

## 15. Credit-card bill-payment app: multi-card payments (a real experiment)
- **Problem**: users with several cards pay 3–4 in the app and the rest elsewhere. User calls said rewards. Budget reality:
  ~₹10–15 per user, not monthly.
- **Ask before solving**: never paid in the app, or churned? Bad experience or organic? Verify call findings with data.
- **Ideas**: streak/incremental rewards per extra card, coins, choose-your-own voucher, personalised vouchers, autopay,
  first-payment offer on a never-paid card. A/B layout: 4 variants + control (~20% each), ramp the winner 40 → 60 → 100%.
- **Shipped experiment**: ₹25 **assured cashback** on long-unpaid cards, via WhatsApp + in-app callouts + payment-page
  strip. North Star = **% of billed cards paid in the app**; secondary = TPV.
- **Metrics built from questions**: comms sent → read → clicked; **payer rate** at 1/2/5 days; funnel discovered → Pay
  Now → paid; discovery of in-app nudges; cost-benefit (cashback vs incremental TPV); **card-level M1/MX retention**
  from the rewarded payment. Cuts by bill amount and payment timing. All test vs control.
- **Outcome**: ~40% drop from discovery to Pay Now, but ~80–90% of tappers paid → awareness was the bottleneck → more
  touch points. Retention +0.5 pts at 2 months, back to normal by 6. Users said "too small" yet redeemed and paid.
  Uplift <1%, so it was **killed**; users said they never registered the reward because **WhatsApp brand messages get
  ignored**. Lessons: behaviour beats sentiment; cashback rarely lifts retention; time-to-market tests (a time-bound
  offer) before a rewards redesign.

## 16. Google Meet whiteboard
The hard part is finding the user for whom it is essential. Professionals already collaborate in Docs/Figma/Miro; the
real need is **school teachers** (one-to-many, writing-based teaching; COVID teachers pointed webcams at physical boards).
Missing this rates "good"; naming teachers rates "great". Don't pick the segment
you know just because it's easier.
Related design-interview examples: **Instagram podcast snippets** (5–10-second cuts for discovery; metrics = adoption,
total time on platform, retention; experience guardrails = upload failures, broken comments, untaken-down hate);
**ATM for visually impaired users** (voice assistant, Braille keypad + voice, image recognition, auto-lock against
robbery; retention driven by safety anxieties).

## 17. Google Flights improvement
- **Clarify the product**: a flight search site on a fares API; **no payments**; redirects to airlines/OTAs and wants to
  be where flight search starts, to earn ads/commission. Positioning: neutral and reliable.
- **Goal**: usage/traffic first (over awareness or redirect conversion).
- **Segments**: undecided destination → trip planning merged with Explore in one journey; decided destination → **price
  optimisers** (matters on expensive international trips) and **first-time route travellers** (don't know layovers).
- **Main feature**: **structured reviews/insights**, not free text: "does this flight get delayed?", "is this layover
  enough?" → "a 1.5 h layover on this route is safe". Weight recent reviews. Draw boundaries with airline partners.
- Valued existing features: price graph, "prices are currently low", price-change alerts. Class idea: move the Continue
  redirect link above the chosen flight.
- Lesson: reviews only matter for the right user; name the user and problem first.

## 18. WhatsApp groups (mock interview)
Narrow in layers: consumer (not Business) → communication → **group** chats (1:1 is solved) → user-created groups.
Segments by why the group exists: friends/family, one-to-many supervised (teacher/students), professional peers. Pains:
people don't respond (shy, can't express in text), overload in one-to-many groups, professional groups need richer
sharing. Metric (should have been confirmed): messages per user per day, or responses per message ÷ group size.
Solutions: AI-suggested replies/stickers; **smart mute with keyword alerts** (people mute/archive groups they still
value); **AI daily summaries**; an **AI avatar** answering FAQs from pinned info; a pre-typed phrase picker for elderly
users who type slowly. Feedback: confirm each step with the interviewer before moving on.

## 19. Swiggy: should it enter medicine delivery? (strategy interview)
5 Cs: fragmented market (PharmEasy, Netmeds, 1mg); strength = delivery fleet; weaknesses = food-tied brand and pharmacy
licensing. Answer: **yes, Genie-style** — pick up from local chemists, don't stock medicines. Design follow-up: the key
feature is **prescription validation** (doctors in the loop, or ML detecting medicine and doctor plus history checks).
Related: **Facebook → travel** fits the *discovery* stage of the value chain (an "add your itinerary" feature), not
booking, transport or stay. **CRED's market** went from near-monopoly to fragmented once BBPS let anyone fetch bills; its
moat became brand and trust.

## 20. PhonePe marketplace from search queries
Data: ~900 top Indian search queries. Task: classify commercial vs non-commercial → bucket commercial queries into
categories → propose a category grid. Method: zero-shot baseline → define "commercial" with examples (one/few-shot) →
add context for secondary products ("tips for storing food" → Ziploc bags) → keep commercial only → icon-friendly names
and a merchandising hierarchy. **Mistake**: ranking categories by raw query volume (travel 68, finance 55) without
filtering commercial intent and matching PhonePe's business model. Sample before bulk.

## 21. Swiggy anti-churn spend and loan default
- Swiggy has ₹1 crore to fight churn: **cluster** users by frequency × recency (frequent + recent; frequent but lapsed —
  target these; new; inactive). Don't pre-name clusters; summarise and name them after.
- Loan default classifier: accuracy misleads (95–98% don't default). Precision 70/100 = 70%; recall 70/85 ≈ 82%. Low
  recall = bad loans; low precision = good customers refused. Pick the trade-off in business terms.

## 22. Capstone exemplars: "increase reviews" on IMDb, TripAdvisor, Goodreads
Six of the nine exemplar decks tackle review volume (three IMDb, two TripAdvisor, one Goodreads). Shared logic: reviews → long-tail SEO traffic + trust → ad
revenue; # reviews = reviewers × reviews per reviewer. Evidence: IMDb's 4× minimum-length rule (600 characters ≈ 10
minutes vs a 3 min 21 s visit); usage gap aware 95% → read 75% → write 4%; reasons (time 67%, no incentive 58%).
Solutions that recur: **guided Q&A or prompt-based reviews** (IMDb Prompts with tag filters for readers; Goodreads forms
+ AI that drafts the review + coins; TripAdvisor View-bot chatbot with one-tap answers), voice-to-text, ML-predicted
nudges after viewing ("did you watch X?"), short-video reviews, reviewer tiers and badges. Pitfalls named: review
quality falls with incentives (tie coins to length/relevance), AI-written reviews feel inauthentic, bots exploit lower
length limits, over-nudging, privacy of cross-app tracking, moderation gets harder with short text. Metric ladders: NSM
reviews/month (or minutes on IMDb) → adoption (% of review-tab openers using prompts) → engagement → performance
(drop-off between prompt selection and submit; time to post) → satisfaction (CSAT) → revenue (ad revenue, DAU/MAU).
Other exemplars: Hotstar mood-lists for discovery (WAS → time to playback start + minimum completion rate); Medium
"Mood Reader" (landing-page test: 142 visits, 80% conversion); Spotify podcast previews and clips (RIED scoring).

