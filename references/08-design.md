# Design for PMs

A PM needn't *do* design, but must understand it well enough to brief designers, critique work and tell great from
good. UX exists to move KPIs: engagement, adoption, task success.

## UX principles
1. **Focus on the user** — you are not your user.
2. **Consistency** — follow platform conventions (Apple HIG, Material). Familiar beats novel for usability.
3. **Hierarchy** — information hierarchy → sitemap → navigation. "Good design is as little design as possible."
4. **Context** — the device, environment and emotion of real use. Test it where users actually use it.
5. **User in control** — actions come from explicit user requests. Advanced options are available but tucked away. Provide confirmations and reset as emergency exits.
6. **Accessibility** — usable by everyone, often legally required, and it simplifies for all users.
7. **Usability testing** — design doesn't end at launch.

## Visual principles
Scale (≤3 sizes; most important = biggest), visual hierarchy (2–3 type sizes, bright vs muted colour), balance
(symmetric = calm, asymmetric = dynamic, radial = centre), contrast (red = destructive; never drop text contrast below
legibility), Gestalt (proximity groups things; similarity, continuation, closure, common region, figure/ground), plus
unity, emphasis, whitespace, repetition (style guide / design system), rhythm. The aesthetic–usability effect: people
forgive minor usability flaws in beautiful designs.

## Flows
Example story: "As a working professional, I want a fast way to buy a single hoodie, so that I save time."
- **Task flow**: one linear path for one task.
- **User flow**: paths with decisions and branches for a user type: the happy path plus alternatives and errors. Judged on conversion. Used for IA/UI design and dev handoff. Name each screen and describe what happens at each step.
- **Wireflow**: wireframes + arrows + annotations. Clearest for stakeholders and devs.
- **User journey**: one persona's experience over time across channels with feelings and pains, for a shared vision and prioritisation. (A flow is screens; a journey is experience.)
Building a flow: what is the user trying to do, what info do they need, what barriers? Match the user objective to the
business objective. Ask for the minimum info in the fewest taps. Measure each step's drop-off, hypothesise a friction
fix, A/B test.
Write flows as explicit actions: "Click Write a Review → Rate → Write text → Submit". Then show only the relevant
screens, focus on interactive elements, and **annotate** what each element does.

## Wireframes
Blueprint of structure, hierarchy, navigation and content, with no visual design. Fast, cheap, disposable. Not a prototype.
- **Ideation phase**: many variations, quantity first. Think separately about structure, layout, content, function.
- **Validation phase**: show several options framed as "here's what I'm thinking", not "this is what we'll build". Invite stakeholder knowledge. Clean up and link screens to tell the story. Narrate what the wireframe can't.
- Conventions: greyscale; colour only for actions/links and semantics (red delete, orange caution). Show input states (error, focus, disabled). Include edge and error cases.

## Fidelity ladder
Wireframe (low-fi structure) → mockup (high-fi visuals: colour, type, spacing) → prototype (interactive, to test with
users before building). Figma prototyping: connect elements to frames; triggers (tap, hover, drag, key) → actions
(navigate, back, open link) → transitions (instant, dissolve, smart animate, push, slide) with easing and duration;
fixed headers/nav on scroll; nested scroll areas; device frames.

## Working with designers
PM = business lens (stakeholders, deadlines, scope, metrics); designer = user lens (IA, interaction, visuals).
Research, testing, MVPs and personas are shared. **The PM owns vision, design and execution**: "if you're not sure whose
responsibility it is, it's the PM's."

**Seven stages of a project with design (owner)**:
1. Initiate work (**PM**): a request, user problem or competitor gap. PM brings the designer in.
2. Align on mission (**both**): PM's PRD/spec/brief **includes a solution point of view with rough PM mocks**. The
   designer questions and signs off.
3. Exploration (**designer**): give room, check in every few days, encourage crazy ideas. **PM sets timelines by
   negotiation** (designer asks 8 days, PM wants 2 → 4–5).
4. Identify direction (**both**): designer brings 3–4 concepts; **PM weighs UX vs cost, feasibility and time** (a GenAI
   concept at +6 months, +5 devs vs a simple input box in 4 weeks).
5. Testing (**both**): prototypes with users. Decide which feedback fits budget and timeline. **Phase it**: ship the MVP
   now and the richer version later rather than not shipping.
6. Prepare for development (**both**): PM **updates the PRD with final mocks, use cases and edge cases** (network drops,
   app closed mid-payment). "The PRD wasn't clear" usually means the PM didn't rework it after design.
7. Development (**feature crew** = PM + designer + dev): kickoff, walkthrough, then a **bug bash** together.

**Design systems**: standard components and rules (Material Design, Apple HIG, company libraries). "99% of the time"
the component already exists; specify it in wireframes. Most PM–designer fights come from PMs not knowing the system.

**Seven principles as the design-review vocabulary**: user-centricity (a seniors' food app: no scratch cards, ≥14–16px
text), consistency (two button styles can measurably hurt), hierarchy, accessibility (WCAG contrast and screen-reader
order; disability can be temporary), user control (back/cancel everywhere; warn before consequential actions;
ways to report problems), simplicity (group in threes; rein in over-illustration), feedback (timely success, progress
and error messages with next steps, never a bare "Error 404"). "99% of your discussion will be around these."

**Design follows segment preferences**: Gen Z/Alpha favour dark and minimal; CRED premium; Flipkart's tier-2/3 bright
"bazaar" colours sell. Surprise at the defining feature = the aha moment. **Unhappy-flow excellence drives retention**
(GPay failure handling, Gmail's "did you forget the attachment?", an app to unlock a suitcase whose code you forgot).
Look for unspoken pains (wire clutter → AirPods).

## Six UX laws with PM uses
| Law | Meaning | PM use / example |
|---|---|---|
| **Jakob's** | users expect your product to work like the others they use | reuse solved patterns (search icon, swipe, cart → checkout, 3-tier pricing); moodboard competitors; differentiate through visual language. Break a pattern only with research (Tinder buttons → swipe) |
| **Hick's** | more choices = slower, more confused decisions | split forms into wizard steps (a Naukri form in 3 steps: +30% completion); one CTA at a time (Amazon checkout) |
| **Goal-gradient** | motivation rises near the finish | progress bars, "200 steps to go", course progress |
| **Von Restorff** | the visually distinct item gets noticed | badges on the target card (Airbnb Superhost; a "Pro" tag drove clicks) |
| **Zeigarnik** | unfinished tasks stick | "profile 5/10 complete" nudges |
| **Miller's** | ~7±2 items in working memory | ≤5–7 visible options (Netflix rows show ~6 tiles) |

## User loads: triage usability feedback in this order
1. **Cognitive** (fix first): thinking, guessing, reading. ("Don't Make Me Think" is by Steve Krug.)
2. **Motor**: clicks, swipes, typing (date slider ~70 clicks → dropdowns 6 → calendar 1–2). Chat-style GenAI UIs carry
   high motor load; **embedded AI** (inline "rewrite: formal") cuts it. "Humans are lazy."
3. **Visual**: clutter hides key elements.
Trade-off rule: accept some visual load to avoid cognitive load (Photoshop's many but clear icons).

## PM wireframing method
- "Every good product manager I met does PM mocks." **Low-fi** (pen and paper) for self-iteration; **mid-fi**
  (Balsamiq, rough Figma) for iterating with the designer and devs — the **PM's ceiling**; **high-fi** is the designer's
  job, even for principal PMs.
- Four steps: (1) write the solution in one line; (2) list the information it must convey; (3) the steps and extra
  requirements (images, skippable, success message); (4) moodboard competitor screenshots → low-fi sketches → mid-fi.
- **Screenshot-crop trick**: screenshot the real app, crop it into sections in Balsamiq, and insert the new element
  (e.g. a premium-trial card). That is the level of wireframe used at Microsoft.
- Staged rollout (5% → 20% → 50% → 100%) on adoption metrics is what most "A/B testing" of designs means in practice.
