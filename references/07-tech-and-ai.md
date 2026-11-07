# Talking Tech: Web Basics, APIs, System Design, ML and LLMs

## Where the PM fits
The PRD (user view: purpose, features, behaviours) goes to engineering, which writes technical requirements
(constraints), which drive system design. The PM doesn't code, but must follow the data flow and trade-offs well
enough to hold the conversation and roughly cost features without waiting for engineering.

## Web and app basics
Why PMs need this: better stand-ups, **PRDs that cover every scenario** (logged in/out, empty response, error, corner
cases), T-shirt-size effort before formal estimates, and judging why an estimate is big. "Tech is your business logic,
not a programming language."
- **Six server types**: web (static content: page structure, logo), application (APIs, dynamic content: feeds),
  database (permanent storage), cache (temporary fast storage), file (images, video, PDFs: S3, Drive), print.
- **Client** = whoever requests. A server becomes a client when it calls another server.
- **Front end**: code that runs in the browser/app (presentation, interaction, API calls). **Visible to anyone**, so
  insecure; deleting an ad in Inspect only changes your local copy. **Back end**: runs on the server, invisible and
  secure (ranking, OTP generation, business logic); builds APIs. **Only the back end talks to the database.**
- **Inspect real calls** in the browser dev-tools Network tab (Swiggy login: `POST /dapi/auth/sms-otp` {mobile, CSRF
  token} → `POST /dapi/auth/otp-verify` {otp, token}).
- **Validate on both ends**: front end for instant feedback and less backend load; back end on submit because the front
  end can be bypassed. **Debounce** checks like username availability (~500 ms after typing stops).

### APIs
- API = a named entry point into someone's code, with a **request payload** and a **response format**; the agreed format
  is the **API contract**. TV-remote analogy: know what each button does, not the electronics.
- Why: **encapsulation** (Swiggy doesn't care how Google computes distance) and **least privilege** (clients see only the
  response, never your DB). Third-party APIs are often priced per call (e.g. per 1,000 calls), so they carry a usage
  cost (Ola built its own maps to cut Google Maps spend).
- **API design method ("government-office peon")**: what information would a clerk need to do this job?
  - Use **IDs, not names**. The logged-in user's ID is optional because the **session** identifies them (sessions also
    power visit and session-duration metrics).
  - Send **only changed fields** on edits (old values are already in the DB); include the object ID (`post_id`).
  - Fire on the commit action (Save), not on opening the editor. "Save" is not a payload field.
  - Response data (names, photos) never goes in the request. Home feed = just {user_id}; ranking happens in the back end.
  - LinkedIn examples: register {email, password, retype}; connection request {recipient_id, message}; edit profile
    {changed fields}; edit post {post_id, changed text}; get comments {post_id}.
- PMs rarely design APIs or schemas, but they read other teams' API docs and specify fields and types in PRDs.

### Databases
Tables of rows and columns. **Primary key** = unique record ID; **foreign key** = reference to another table's PK
(accounts.user_id → users). Bank transfer as a PM spec: authenticate → validate balance → write debit and credit
records → respond. Normalised (smaller, targeted) tables give faster queries. Metrics and reports come from the DB.

### Scaling, load balancing, caching
- **Load balancer** spreads requests over a server pool running the **same code version**. Algorithms: round robin,
  weighted round robin, least connections, least average response time.
- **Horizontal scaling** (add servers): no downtime, good for temporary peaks (sales, concert tickets). **Vertical**
  (bigger machines): usually needs a restart; for DB growth or slow per-request processing. Flipkart's first Big
  Billion Days crashed.
- **Memory (RAM) is fast and temporary; storage (disk) is permanent.** Cache what changes rarely (a 4.2 rating from 8.4k
  ratings). **Browser/device cache** for logos, fonts, images; **in-memory server cache** (Redis, key-value).
  **Read-through**: app → cache → miss → DB → write to cache → respond. Staleness fixes: **TTL**, or update the cache when
  writing the DB (can be async).
- **PM relevance**: the PRD states freshness needs ("ratings may refresh hourly") and response-time targets worked
  backwards from the user (wallet balance in <~1 s); engineering decides cache vs real-time.
- **Feeds mix pre-computed and real-time**: LinkedIn ranks recent posts by stored affinity scores; "People you may know"
  is pre-computed.

### Vocabulary engineers will use 
- **Library** (someone's code for one narrow job, e.g. date formatting; same language as your app) vs **framework**
  (architecture for the whole app: React, Angular, Django) vs **SDK** (platform toolkit: Android Studio/Xcode with
  compiler, simulator, debugger, device APIs). "Which framework?" is a team-familiarity call more than a quality call.
- **JSON** is the payload format between client and server (key–value pairs, arrays).
- **Compiler** (translate all code up front; fast; hides source) vs **interpreter** (line by line at run time; flexible).
- **DOM**: the browser's tree of page elements; JavaScript changes the page through it.
- **Component architecture**: pages are built from loosely coupled components (parent fetches data, passes it to
  children). Loose coupling is why some UI changes are cheap (swap one component) and others are expensive (logic
  tangled across components). **MVC**: model (data + business logic), view, controller.
- **Single-page apps** load once and then fetch only data, so navigation feels instant but the user's device does more
  work. Engineers prefer **few back-end calls**: fetch once, process on the device.
- **Storage intuition** for estimates: a text document ≈ KB, a photo ≈ MB, 1,000 photos ≈ GB, a million ≈ TB.
- **IP addresses** give approximate location but change often, so blocking abusers by IP is weak; IPv4's ~4.3B
  addresses are running out (IPv6 rollout is slow because hardware must change).

### Worked system design: Tinder (registration, potential matches, swipe, match)
- Tables: `users` (photo URLs, lat-long, DOB), `potential_matches` (refreshed daily by ML), `swipes` (swiper, swipee,
  like/pass, timestamp), `matches` (match time = the second like).
- **Register**: client → LB → app server → upload photos to **file storage first** to get URLs → write the user record
  with URLs → respond. The DB never stores image files.
- **On launch**: get potential matches → cache miss → DB reads IDs, then metadata from `users` → write the next 5–10 to
  cache → respond → **client fetches images by URL** from file storage and keeps them in the device cache.
- **Swipe API**: {swipee_id, type}; the server stamps the time. Write the user story first. "None of it is tech; it's
  your core functionality."
- For PMs, **APIs and the database matter more than the infra diagram**. System design = flow/architecture + DB design
  + APIs.

## Requirements
- **Functional**: what users can do. Uber: see nearby cabs with price and ETA, book, track the driver, cancel.
- **Non-functional ("-ilities")**: availability, reliability (no lost uploads), latency, scalability, performance, security, maintainability.
- Quality attributes are business trade-offs. Sports betting wants speed over asset quality; Instagram wants quality
  over speed. Enterprise wants reliability (slow, gated releases); consumer wants delight and fast iteration.

## 6-step system design (also the shape of a PM tech-round answer)
1. Clarify requirements (functional + non-functional; narrow scope).
2. Estimate scale: users → requests/sec, storage, bandwidth. URL shortener: 500M/month × 60 months × 100 B ≈ 3 TB. Uber: 5M users × 5 actions/day ≈ 58 RPS.
3. **Data model and data flow** ("if unsure where to start, start with the data flow"): entities, SQL vs NoSQL, blob storage for media.
4. High-level components (5–6 boxes). Google Drive: file processing, metadata, notification service, cloud storage.
5. Detailed design and trade-offs: partitioning, hot users, caching, load balancers.
6. Bottlenecks: single points of failure, replicas, redundancy.
Quick version: quality attributes → components (client, web server, DB, asset server/CDN) → load per component.
Context diagram (system + external actors such as user and bank) → data flow diagram (login → user DB → catalogue → content DB → play).

Vocabulary to recognise: MVC (view = touchscreen, controller = operator, model = burger/data); monolith →
service-oriented architecture; API; load balancer; cache (Redis); queue/stream (Kafka); WebSocket; sharding and
consistent hashing; CDN; SQL (MySQL, Postgres) vs NoSQL (document, key-value, column: Mongo, Cassandra) vs in-memory vs
graph DBs. Build vs buy vs reuse; factors: scale, time to deliver, cost, team familiarity and ecosystem,
maintainability, reliability, scalability.
Uber case features: supply service (drivers ping GPS every 4s), demand service, dispatch matching on map cells (S2), ETA on the
road graph incl. cabs about to finish, failover using state digests stored on driver phones, analytics for fraud and
incentive abuse.

## ML in products
- Supervised (labelled → predict: recommendations, spam, price, credit), unsupervised (structure: clustering songs by
  mood, segments), reinforcement (reward-driven: robotics, driving).
- Algorithm-to-use-case map: linear regression (estimate a value), logistic regression (yes/no class), decision tree
  (interpretable decisions such as credit), KNN (similarity recs), SVM (text/image classification, moderation).
- Lifecycle: spot the opportunity (repetitive tasks, complex analysis, personalisation) → **data quality and quantity**
  → train and evaluate → integrate, monitor, iterate.
- PM risks: data bias (unrepresentative training data), explainability (black boxes erode trust), cold-start or missing
  data (a solution can fail feasibility purely on data — Spotify activity-recs scored 1 for feasibility).

### ML literacy for PMs
- **Rules vs ML**: hand-coded fraud rules ("2FA for Turkey", then Vietnam…) never end; ML learns the rules from labelled
  history and is retrained as patterns shift. "Give me past data, I'll figure out the rules."
- **AI ⊃ ML ⊃ deep learning ⊃ GenAI.** **Output-type test**: a number, class or probability → predictive ML (Netflix
  recommendations, search ranking); human language, image, audio or video → GenAI (AI Overviews). Narrow AI does one
  task well; AGI is a continuum, not a threshold.
- **Why PMs need it**: size opportunities with classifiers on samples without engineers (Google "multi-day queries");
  realistic timelines (feature extraction alone can take six months); ML-driven optimisation (Gmail's Updates tab,
  discount levels); spotting GenAI opportunities (AI Overviews, AI drafting). Facebook-scale moderation is 95–98%
  automated; PMs own model choice, integration and latency.
- **Problem → ML type**:

| Need | Type | Example |
|---|---|---|
| Predict a number | supervised **regression** | Cashify used-phone price; house price |
| Predict a class | supervised **classification** (binary / multi-class) | loan default; fraud; Gmail tabs; review sentiment |
| Find unknown groups | unsupervised **clustering** | Swiggy anti-churn: frequency × recency clusters; auto-categorising products with no categories |
| Find co-occurrence | unsupervised **association** | aisle placement (milk, bread, eggs) |
| Compress features | dimensionality reduction | 100 features → 10 |
| Adapt from rewards | **reinforcement** | adaptive tests (GMAT), game difficulty, trading |

  Test: needs past data with known outputs → supervised; raw data without outputs → unsupervised. Clustering often
  precedes classification (name the clusters, label, then train a classifier). Pick cluster count with the silhouette
  score and sanity-check with the business.
- **Vocabulary**: training data + labels; **feature engineering** (drop name, combine weight + height into BMI, savings
  = income − expenses); train/test split (e.g. 80/20; test = the held-back exam); **overfitting** (memorised, fails when
  behaviour shifts) vs **underfitting** (too simple, consistently mediocre).
- **Lifecycle**: features + labels → split → feature importance → algorithm by output type → train → evaluate → deploy →
  monitor.
- **Evaluation in business terms**:
  - Regression: **MAE** (mean absolute error; signed errors cancel) or RMSE; compare models on it.
  - Classification: **accuracy misleads with imbalance** (95–98% of borrowers don't default). **Precision** = of those
    flagged, share truly positive; **recall** = of true positives, share caught. They trade off and don't sum to 100%.
    Translate each error: low recall = bad loans approved; low precision = good customers refused (lost revenue).
- **PM's say on features**: flag inputs that aren't controllable or don't make sense. Recommenders are usually hybrid
  collaborative + content filtering.
- GenAI "doesn't know right from wrong and gives the simplest answer": verify output.

## Is an LLM right for this?
**Intern test (Andrew Ng): could a fresh graduate do it with detailed instructions? If yes, try an LLM.** Good fits:
writing, summarising, extracting, classifying, rewriting, Q&A over provided text, conversational interfaces.
How it works: it predicts the next token repeatedly. It doesn't "understand", but next-token training captures enough
language structure to look like it does. Few-shot, in-context examples steer it (GPT-3).
Mental model (Karpathy): LLM = kernel of a new OS (context window = working memory, tools, retrieval). Fast "system 1"
by default.

### LLM concepts a PM should use in conversation
- **NLP pipeline**: tokenisation → cleaning (normalisation, stop words, stemming/lemmatisation) → POS tagging, NER,
  TF-IDF → **embeddings** (similar meanings sit close: "chole bhature near me" ≈ "Indian food near me") → next-token
  prediction. Old NLP read left to right with tiny context and no memory of earlier turns.
- **Attention / self-attention** (focus on informative words: "where to find Prada shoes for men" ≈ "Prada shoes men");
  **Transformer**; **GPT** (generative pre-trained transformer) vs **BERT** (bidirectional).
- **Context window** = tokens considered at once. In-chat "learning" is the context window, not persistent learning
  (a rule set in one chat is gone in a new one).
- **Temperature**: ~0 for factual/deterministic tasks (translation, summarisation); higher for creative variety.
- **Hallucination** is worse in data-sparse domains. **Quality tracks training data per language**: English > Hindi >
  Konkani; check Indic-language coverage before promising features.
- **Quality bar**: golden examples (50–100 ideal responses) + human evaluation for quality and factuality.
- **Build vs buy**: companies usually take **API access** (Gemini, OpenAI) or open weights (Llama), then **fine-tune**
  with domain prompts and examples, **align/post-train**, **evaluate** (factuality, correctness, tone) and launch.
  Pre-training is rarely worth it. Fewer parameters = faster, narrower models that degrade outside their domain.
  Prototype in **Google AI Studio** (model, data, temperature, tokens).

## Prompt iteration loop
Initial prompt → run on a **sample dataset** (historical or synthetic) → analyse errors → revise → repeat until the
quality bar is met. Techniques: clear instruction, context, question framing, exemplars (few-shot). Break complex tasks
into steps. Version prompts; they are product configuration. Experiment on them like any feature (see 05: test the
configuration, measure downstream behaviour).

**Zero / one / few-shot**: zero-shot = ask directly (fine for well-known tasks); one-shot = one labelled example;
few-shot = several examples in the exact output format. Escalate when labels are novel or ambiguous: zero-shot
baseline → **define your terms** ("commercial query") → add examples → inspect failures → add context (count secondary
products: "tips for storing food" → Ziploc bags). **Sample before bulk** (don't paste 900 rows first). Plain, simple
language works better. Ask for a **reason with each label** so outputs can be audited. Adding context is not one-shot;
one-shot is an example of the expected labelling. Most people only ever zero-shot and accept the first output.
PM uses: classify search queries into commercial categories for a marketplace; categorise competitor app-store reviews
with a sentiment score; mind maps and sitemaps/wireframes (Claude, Relume) **after** you've done the thinking yourself,
as a reviewer — you can't judge AI output on work you've never done.

## LLM failure-mode checklist (put in every AI PRD's risks section)
| Risk | Mitigation |
|---|---|
| Context/token limits | condense, chunk, route to smaller specialised models |
| Hallucination / inaccuracy | evals against reference data, human-in-the-loop on high-stakes output, citations/grounding, domain checks, feedback loop |
| Stale knowledge (training cutoff) | retrieval (RAG) for fresh data, scheduled updates, user flags |
| No long-term memory | session memory, user profile/context store, DB-backed memory |
| Multi-step reasoning errors | decompose, rule-based checks, human review |
| Idiom, sarcasm, context misreads | diverse examples, context-aware design |
| Privacy leakage | anonymise inputs, minimise data sent, differential privacy, federated or on-device processing |
| Bias / stereotyping | representative data, bias audits |
| Security | jailbreaks, prompt injection (untrusted content steering the model), data poisoning |
| Ethics / accountability | transparency, clear human ownership of decisions |
LLMs augment human judgement. Design the human checkpoint wherever errors are costly.
