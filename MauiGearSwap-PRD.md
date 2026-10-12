# MauiGearSwap.com — Product Requirements Document

**Version:** 0.2 | **Date:** October 11, 2026 | **Status:** Draft for product review  
**Release:** Kihei MVP pilot | **Product owner:** TBD

## 1. Basis and decision status

This PRD translates *MauiGearSwap.com — Draft Business Plan v0.3* (20 pages) into product requirements. Source page references below refer to that PDF. The document's product proposals are treated as source material; its outreach and advertising instructions are not authorization to execute those activities.

**Source requirement** means explicitly described in the business plan. **Proposed specification** means a detail added to make the product implementable or measurable, pending owner review. **Open decision** means the source does not resolve the issue. All priorities and acceptance criteria are proposed elaborations unless stated otherwise.

The source's tourism figures and external references are explicitly unverified in its export (p. 20). They are not relied on as validated evidence or launch requirements here. This PRD does not select a technology stack or establish a delivery date.

**Revision 0.2:** Adds a proposed Maui Gear Assistant for optional gear search and listing preparation, an admin assistance experiment, and linked user flows. AI features are P1 enhancements; core marketplace launch does not depend on them. No AI vendor or stack is selected.

## 2. Product summary and problem

MauiGearSwap.com is a local classifieds marketplace where travelers can buy, sell, give away, and find free vacation gear. The initial market is Kihei on Maui. Visitors can acquire gear near their accommodation, use it during their stay, and sell or pass it on before departure.

Travelers need bulky items temporarily. Buying new, renting, and flying with equipment can be inconvenient, while departing visitors often have usable gear they no longer need. Generic marketplaces do not foreground the pickup timing and departure constraints that determine whether a traveler can complete an exchange.

**Value proposition:** “Get it free or buy it. Beach it. Pass it on.”

**Pilot hypothesis:** Travelers in Kihei will use a simple marketplace to find and exchange vacation gear when inventory, pickup location, and availability overlap. The pilot must validate completed exchanges and operational cost, not merely traffic. (Source pp. 1–5.)

**AI objective (new proposal):** Reduce effort to find suitable real inventory and prepare accurate listings. Evaluate whether assistance improves listing completion and reported exchanges without increasing incorrect information, coordination failures, or operating cost beyond agreed limits. AI cannot substitute for real inventory.

## 3. Users and jobs to be done

| User | Primary job | Product success |
|---|---|---|
| Arriving traveler or family | Find affordable or free usable gear near the stay and within a pickup window | Contacts a relevant seller and completes pickup |
| Departing traveler | Sell or give away gear before leaving | Publishes promptly and closes the listing before departure |
| Resident, host, or property manager | Redistribute unused or leftover gear | Can list and manage multiple items without a public profile |
| Pilot administrator | Maintain useful, current inventory and handle abuse | Reviews listings, resolves reports, and detects service failures |

Primary visitors typically need gear for 3–14 days; hosts and residents are secondary supply sources. (Source pp. 2–4.)

## 4. Goals, scope, and priorities

**P0:** Required before opening the public pilot. **P1:** Included in the MVP plan but may follow the core release if explicitly deferred. **Later:** Outside the free pilot.

### P0 launch scope

- Responsive website focused on Kihei; browsing and search without an account.
- Search-first landing page, separate results page, and listing details.
- Paid and free item listings with actual photos, condition, pickup area and windows, and departure timing.
- Email verification and passwordless access to the seller's own listings.
- Submission, prepublication moderation, correction, closure, and automatic expiry.
- Asynchronous buyer inquiry flow; no real-time chat required.
- Reporting, admin moderation records, core operational alerts, and exchange analytics.
- Listing rules and category restrictions, including disabled snorkel gear until review criteria exist.

### P1 MVP enhancements

- One optional Maui Gear Assistant with “Help me find gear” and “Help me list gear” entry points. Ordinary search and listing forms remain fully usable.
- A small admin assistance experiment that summarizes review evidence without making moderation decisions.

- Optional update subscriptions with separate consent and unsubscribe.
- Distance filtering and sorting when usable location data exists; area filtering is required at launch.
- Optional brand, bundle metadata, and structured damage notes; sellers must still disclose condition in the core form.
- Expanded automated text/image screening beyond file validation and basic abuse checks. The source proposes automated screening; capability and cost must be resolved before deciding whether to defer it.

### Outside the MVP

Native mobile apps; platform processing of gear payments; transaction fees; paid promotions or subscriptions; public seller profiles; ratings and reviews; real-time chat; rental booking; delivery logistics; expansion beyond the initial service area. Reservation or escrow behavior is not defined in the source and is excluded from this proposal.

Future monetization may cover optional promotions only. The source's $2 promotion price is a hypothesis, not a committed price; $1,000 monthly promotion revenue is an illustrative scenario, not a pilot target. (Source pp. 4–6, 16, 19–20.)

## 5. Core user journeys

1. **Find gear:** Open landing page → submit search or select suggestion → filter results by pickup timing and area → inspect listing → send inquiry → arrange pickup directly → optionally provide outcome feedback.
2. **List gear:** Select List gear → enter details and photos → provide email → verify email → listing passes checks and admin review → publish → receive inquiries → arrange exchange → mark sold or given away.
3. **Manage gear:** Request email sign-in → open owned listings → edit, respond to correction request, or close listing. Material edits require review before republishing.
4. **Moderate:** Open pending queue → inspect photos and risk flags → approve, reject, or request correction with reason → handle reports and stale inventory → record resolution.

Buyers pay sellers directly at pickup. Free items change hands without payment. An inquiry does not establish an exchange or reserve an item. (Source pp. 9–10, 16–18; reservation statement is proposed.)

Detailed alternate paths, confirmations, failures, and requirement mappings are specified in [User Flows](/Users/dinok/Documents/MauiGear/MauiGearSwap-User-Flows.md). Assisted search joins the normal results/detail/inquiry journey; assisted listing joins the normal form/verification/review lifecycle. Drafting inquiry messages and preparing departure resale drafts are later features, not first-release assistant capabilities.

## 6. Functional requirements and acceptance criteria

### FR-01 — Landing page and search submission [P0]

**Source:** pp. 7–8. Header contains the brand and List gear action. Use the supplied headline, tagline, “What do you need?” input, and Search button. Suggested searches are Beach chairs, Coolers, Strollers, Camping gear, and Free gear. Keep the page free of listing grids, promotional banners, and long explanations.

**Acceptance:** Enter and Search open a separate results page with trimmed query text. Typing alone does not navigate. An empty or whitespace-only query stays on the landing page with a helpful prompt. Suggestions submit immediately; Free gear applies the Free-only filter. Suggestions are described as curated, not popular without data.

**Optional assistant entry:** “Help me find gear” opens a user-initiated assistant surface. It does not replace the landing page on typing or add a compulsory conversation.

### FR-02 — Results, filters, and sorting [P0; distance P1]

**Source:** pp. 6, 8–9. Match title, category, and description. Search only published, unexpired, available listings. Show submitted term and result count. Primary controls: pickup area, dates, Free only, sort. More filters: category and price range. Support today, this week, custom pickup date/time, and seller leaving soon. Default sort is newest; offer price and departure date, with distance only when supported.

**Acceptance:** Each card shows photo, title, price or Free, area, condition, pickup window, and departure timing. Sold, given-away, unavailable, expired, pending, rejected, and removed listings never appear. URL parameters preserve query and filters across reload, sharing, and return from details. Show loading, no-match, and retryable failure states while retaining input. Mobile cards stack in one column with secondary controls grouped under Filters.

**Proposed date rules:** Interpret pickup times in Pacific/Honolulu and label them as Maui time. A date/time filter matches when a listing has a future pickup interval overlapping the requested interval. Hide a listing when no future pickup window remains even if its expiry job is delayed. Define “this week” and “leaving soon” in the UI once their thresholds are selected. Never require device location; fall back to pickup-area controls.

### FR-03 — Listing detail and unavailable state [P0]

**Source:** p. 9. Display all photos, description, price/Free, condition, pickup location, available window, departure date, Contact seller, and Report listing.

**Acceptance:** A direct link to an inactive listing displays an unavailable state and a route back to search; inquiry is disabled. Public content contains no seller email or private pickup address under the proposed privacy model. Relative timing agrees with results and Maui local time.

### FR-04 — Listing creation and validation [P0]

**Source:** pp. 9, 16–17. Require photos, title, category, price or Free, condition, pickup area, available dates, departure date, contact preference, and verified email. Description is displayed and searchable; this PRD proposes requiring it. Optional: brand, bundle, damage/wear notes.

**Acceptance:** Missing or invalid fields block submission with field-level guidance and preserve entered information. Free is an explicit choice; paid price must be positive. At least one readable actual-item photo is required. Disabled categories cannot be submitted. Dates cannot produce a pickup interval after the applicable listing deadline. No listing publishes until email verification and administrator approval are complete.

**Open:** Photo quantity, formats, upload size, field limits, condition vocabulary, price ceiling, and whether local sellers use a departure date or an explicit listing end date.

**Optional listing assistance:** “Help me list gear” prepares suggestions for the ordinary listing form under FR-13. User review, validation, verification, and moderation remain required.

### FR-05 — Identity and listing ownership [P0]

**Source:** pp. 5, 9, 16. Create the account on demand for first-time listing submission; returning sellers access listings by emailed secure link or one-time code. No public profile required.

**Acceptance:** Verification succeeds before publication. A seller can view and modify only their own listings. Proposed links/codes are time-limited, single-use, and rate-limited. Invalid or expired credentials offer a new request. Delivery failures preserve the submission and provide retry guidance. Administrators have separately restricted permissions.

### FR-06 — Buyer inquiry [P0]

**Source:** p. 10 permits an internal form, masked relay, or form emailing the seller.

**Proposed MVP choice:** Asynchronous inquiry form delivers an email to the seller. Collect buyer reply email, message, and intended pickup window. Do not require a full buyer account. Resolve reply routing and whether buyer email verification is required before implementation.

**Acceptance:** Only active listings accept inquiries. Apply posting/inquiry abuse limits and validate input. Show success only after durable acceptance for delivery, distinguishing delivery failure from submission failure. Include listing and pickup context in the seller notification. Keep contact information out of public pages and analytics. Track accepted inquiries separately from delivered notifications and completed exchanges.

### FR-07 — Seller management and listing lifecycle [P0]

**Source:** pp. 5, 16–18. Owners can mark sold, given away, or unavailable. Listings expire after departure. Material edits require recheck.

**Proposed states:** Pending verification → Pending review → Active → Sold / Given away / Unavailable / Expired. Review may instead produce Needs correction or Rejected; an administrator may mark a listing Removed. Terminal states remain distinct for reporting. A material edit to an active listing returns it to Pending review and hides it until approval.

**Acceptance:** Closure immediately removes the listing from search and disables inquiries. Closure records reason and time; unavailable does not count as an exchange. Scheduled expiry has retry/monitoring and search also enforces the deadline. Changing a pending submission cannot bypass review. Reopening a closed listing is not automatic and requires a defined review policy.

**Proposed expiry:** Expire at the earlier of final pickup availability and the seller deadline. If only a departure date is captured, use end of that Maui calendar day provisionally. Exact departure times and local-seller expiry remain open decisions.

### FR-08 — Listing and photo moderation [P0; advanced automation P1]

**Source:** pp. 10, 16–17. Every pilot listing and its photos receive admin review. Validate files; flag missing, unreadable, irrelevant, repeated, or inconsistent images and suspicious text. Request a current photo with a site-issued code when authenticity is uncertain. Screen item category, condition, damage, and prohibited-item risks.

**Acceptance:** Pending content remains private. Admin can approve, request corrections, reject, or remove, recording actor, time, and reason. Uncertain items remain held. Automated checks assist review and never independently certify safety or ownership. Material edits repeat required checks. Sellers can see correction/rejection reasons through secure access.

### FR-09 — Reports, admin monitoring, and alerts [P0]

**Source:** pp. 10, 17–18. Allow listing reports and monitor inventory, reviews, inquiries, complaints, no-shows, feedback, and service health.

**Acceptance:** Each live listing has a report action with category and explanation. Reports enter an admin queue with open, in progress, and resolved statuses (proposed). Suspected fraud/unsafe-item reports trigger an admin alert. Monitor duplicate bursts, repeated check failures, review backlog, email delivery, uploads, and expiry failures. Record issue actions and resolutions. Alert thresholds are configurable and tuned during the pilot; designate an owner before launch.

### FR-10 — Category controls [P0]

**Source:** p. 6. Initial taxonomy: beach chairs, umbrellas, coolers, boogie boards, kids' beach toys, beach wagons, camping gear, hiking gear, fishing gear, strollers/permitted family travel equipment, surfboards, and paddle boards. Beach items lead acquisition but do not limit permitted inventory.

**Acceptance:** Admin can disable categories; listing rules apply within every category. Snorkel gear stays disabled until hygiene and condition criteria are approved. Final prohibited items and permitted family/sporting equipment require a launch decision; inclusion of a broad category does not automatically allow every item in it.

### FR-11 — Update subscription [P1]

**Source:** pp. 5, 9. Updates require separate opt-in and email verification; no paid plan.

**Acceptance:** Listing submission does not silently subscribe users. Store consent and verification; allow unsubscribe. Do not expose an opt-in until the type and frequency of updates are defined.

### FR-12 — Assisted gear search [P1; new proposal]

Allow natural-language requests such as “Two beach chairs under $40 in Kihei tomorrow afternoon.” Parse the request into editable query, category, area, budget, and Maui-time pickup filters. Clarify whether budget applies per listing or to the requested total, and confirm quantity from explicit listing data; do not assume one listing contains two chairs.

**Acceptance:**

- Show interpreted filters and the exact date/time interval. Ask a focused clarification for material ambiguity, including undefined “afternoon,” location, or budget semantics. Do not invent an exact address or silently relax constraints.
- Retrieve only eligible real listings through the same backend rules as ordinary search. Every recommendation links to its listing; price, condition, and pickup claims come from stored listing data. Seller-entered claims remain seller claims, not AI verification.
- Price, time overlap, status, category eligibility, and quantity checks are enforced by application logic. AI text cannot bypass them. If quantity is unknown, show that uncertainty rather than claiming a match.
- Show actual results using the standard results page and shareable normalized filters. Preserve confirmed filters when users switch to ordinary search. Changing filters reruns retrieval; stale suggestions are revalidated at detail/inquiry.
- Distinguish no matches from service failure. With no matches, propose specific broadened filters and apply only after user choice. With failure, timeout, quota exhaustion, or disabled AI, offer ordinary search without losing confirmed input.
- Browsing and assisted search require no account. Do not collect a full travel itinerary when pickup area/window is sufficient.

### FR-13 — Assisted listing preparation [P1; new proposal]

Use seller-provided notes and current actual-item photos to suggest title, permitted category, and description. Ask for missing information. Clearly distinguish suggestions from seller-confirmed facts and allow editing or rejection of all suggestions.

**Acceptance:**

- Seller explicitly confirms price or Free, condition and damage, pickup area/windows, and departure or applicable end date before submission. Do not preselect a paid price, infer a departure, or claim absence of damage from a photo.
- Uncertain brand, dimensions, quantity, ownership, hygiene, or physical safety are omitted or raised as questions. Preserve disclosed defects; do not embellish condition or modify listing photos to hide wear.
- Suggestions transfer to a preview/form only on user choice. The ordinary submit action sends the confirmed form into the existing email verification and admin-review process; the assistant has no publication permission.
- File and category validation remain enforced by the application. Snorkel remains disabled. AI failure preserves user-entered information and offers manual completion; photo upload can be retried independently.
- No completed exchange, sold state, or reservation is inferred from a conversation or photo.

### FR-14 — AI-assisted admin review [P1 experiment; new proposal]

For authorized administrators, summarize listing content and flag potential missing disclosures or photo/text inconsistencies with references to the relevant field or photo. Treat findings as fallible suggestions.

**Acceptance:** Admin sees underlying evidence, can ignore or correct a flag, and records the final decision/reason. AI cannot approve, reject, remove, resolve reports, or certify safety. AI failure leaves the manual queue available and does not change listing status. Review already holds the listing pending; an AI flag is not an independent enforcement action.

### FR-15 — Assistant permissions, grounding, and recovery [Required for any enabled AI feature]

Use a small allowlist: search public eligible listings, read public listing details and approved help content, and produce draft suggestions. Admin evidence tools are isolated from public sessions. The public assistant cannot read other users' private drafts, contact data, or moderation records.

**Acceptance:**

- Backend authorization determines actor, permitted tool, target record, and operation. Prompts are not access control. Model output never supplies trusted identity or permission.
- In the first AI release, marketplace mutations and outbound messages use ordinary UI workflows. Publishing, price changes, closure, and inquiry sending cannot be executed autonomously by the assistant. Any later write tool must show the exact action/target/content, require explicit confirmation, and revalidate permission and current record state.
- Treat user messages, listing text, photos, and tool results as untrusted data. Instructions embedded in them cannot grant permissions or override marketplace rules. Test cross-user access and malicious instructions.
- Ground marketplace help in approved current rules; say when an answer is unknown and offer the support route. Do not invent inventory, guarantee pickup, negotiate for a seller, or promise resale proceeds.
- Inform users when they are using AI. Minimize data sent to providers; exclude credentials and unnecessary contact/address information. Select provider handling, consent/notice, and retention/deletion policy before enabling the feature.
- Maintain redacted tool/action/error records and versioned prompts/model configuration for evaluation. Set per-session limits, bounded retries/timeouts, a configurable spending cap, and an admin disable switch. At a cap or outage, preserve core marketplace functionality.

## 7. Data and nonfunctional requirements

**Proposed minimum records:** User (verified email, role, consent); Listing (owner, content, category, photos, price/Free, condition, area, pickup intervals, seller/end deadline, status and timestamps); Inquiry (listing, reply contact, message, preferred window, delivery status); Report; Moderation action; Operational issue; Analytics event. Coordinates are optional. Store enough state history to reconstruct closure and review metrics.

- **Privacy:** Public pickup area; precise meeting details exchanged privately. Never publish email addresses. Define data retention and account deletion before launch.
- **Security:** HTTPS, protected admin access, ownership checks, upload validation, sanitized content, and rate limits. Authentication secrets must not enter logs or analytics.
- **Accessibility:** Proposed target is WCAG 2.2 AA; key forms and search must work with keyboard navigation, labeled controls, visible focus, and readable errors.
- **Mobile usability:** Search, listing, inquiry, and closure work on a narrow phone screen; use an initial 360 px test viewport.
- **Performance:** Proposed target is usable main content within 3 seconds on an agreed representative mobile connection; confirm measurement method and image limits before build.
- **Reliability:** Persist submissions and inquiries before confirmation; provide recoverable failures. Back up records and verify restoration before pilot. Monitor expiry and notification jobs.

**AI records and reliability:** Store only the assistant context needed for the chosen retention policy: normalized filters, suggestion provenance, user acceptance/edit events, model/prompt version, latency, usage/cost, and redacted errors. Do not default to retaining raw conversations or photos in AI logs. Anonymous sessions do not become public profiles. User-confirmed listing fields are the source of truth. Define a response timeout and hard usage budget before rollout; core search must not wait on an AI service.

These are proposed engineering requirements, not commitments found in the business plan. Hosting, vendor choices, service-level targets, and moderation response time remain unselected.

## 8. Measurement and success criteria

Source targets (pp. 18–19) are pilot goals rather than software acceptance criteria. Measure from the public pilot start date, which is TBD.

| Measure | First 30 days | First 90 days |
|---|---|---|
| Inventory | 50–100 active listings | 500 listings created |
| Reported exchanges | 25 sales + free pickups | 150 sales + free pickups |
| Repeat supply | 10 sellers listing more than one item | Evidence of repeat activity in Kihei |
| Host development | 3 host/manager conversations | 3+ host/manager partnerships |
| Exchange share | At least 30% sold or given away | Track trend; source sets no target |
| Learning | Identify top 3 categories and recurring user problems | Test promotion willingness to pay and measure operating cost |

**Proposed definitions:**

- Active listings: approved, available, unexpired real listings at a specified snapshot; additionally report daily average to avoid a misleading single-day count.
- Reported exchange: unique listing first marked Sold or Given away. Report both totals separately. Offline payments mean these are self-reports, not verified transactions.
- Exchange share: listings published in a defined cohort subsequently marked Sold/Given away, divided by all real listings published in that cohort. Show observation window and unresolved listings; evaluate the 30-day cohort again after its listings expire.
- Repeat seller: verified user with at least two distinct published real listings, excluding corrections and duplicates.
- Search-to-contact: search sessions with at least one accepted inquiry / eligible search sessions. Report no-result sessions separately.
- Contact-to-exchange: unique inquired-about listings later reported exchanged / unique inquired-about listings, with a stated follow-up window; this does not prove attribution to a particular buyer.
- Time to exchange: elapsed time from first publication to reported exchange. Before-departure exchange: reported exchange timestamp at or before seller deadline, for listings with that deadline.

Instrument landing visits, search submissions/results counts, filter use, listing views, inquiry acceptance/delivery, submission/verification/review/publication, closures, expiry, reports, and subscription consent. Track review time, no-shows/complaints, top categories/areas, cost per inquiry/listing, support hours, hosting, and marketing costs. Avoid personal contact data in event payloads. Exclude administrator tests, examples, and demo inventory from all liquidity metrics.

**AI evaluation (new proposal):** Compare assisted and ordinary flows by task completion, search-to-contact, listing abandonment, correction rate, time to publish, and reported exchange rate. Define acceptance as a user choosing to apply a suggestion; measure later edits separately. Track recommendation factual errors, invalid/stale result rates, unauthorized-action attempts, fallback rate, latency, cost per completed assisted task, and moderation minutes per listing. Comparisons must report sample sizes and user-selection differences; voluntary AI users alone do not establish causal improvement. Use a controlled rollout where feasible. Preserve existing exchange definitions and do not count assistant conversations as inquiries or exchanges.

**Proposed pilot decision:** Continue or expand only after reviewing exchange targets, repeat supply, pickup friction, moderation capacity, and cost together. If traffic rises without exchanges, investigate inventory/timing fit before expanding geography or adding paid services. The business plan provides no automatic go/no-go threshold beyond its targets.

## 9. Launch plan and release acceptance

**Source launch approach:** Seed 20–50 real listings in Kihei, help early sellers, engage hosts/managers, then test Search ads. The plan proposes $10–$25/day for 2–3 weeks, within an initial overall budget target of $2,000–$5,000. These are planning inputs, not authorized spend. Example inventory must be clearly labeled; this PRD proposes excluding it from live buyer search and placing it only in a demo context. (Source pp. 10–15, 18.)

**Proposed sequence:**

1. Resolve launch decisions, finalize listing rules, pickup areas, moderation ownership, and inquiry flow.
2. Deliver search, posting, secure access, moderation, inquiry, closure, expiry, and measurement.
3. Test privately with hosts/sellers and seed real inventory.
4. Open the Kihei pilot and follow the source's four-week acquisition/learning plan. Launch-critical date filters precede opening; later improvements may follow feedback.
5. Validate assistant behavior on a fixed scenario set, then enable a limited P1 rollout after privacy, cost, permissions, and fallback decisions are resolved. AI must not delay real inventory seeding.
6. Review 30-day and 90-day outcomes before expanding or monetizing.

**P0 release checklist:**

- Complete buyer, seller, and admin journeys pass on mobile and desktop.
- Unverified/unapproved/expired/closed listings cannot appear in search or receive inquiries.
- Free, paid, date overlap, boundary time, and shareable-filter behavior are verified.
- Owner isolation and administrator permissions are verified.
- Broken uploads, failed email delivery, invalid sign-in links, duplicate submissions, and expiry delays have recoverable states.
- Reports and operational failures reach a designated admin; moderation actions are recorded.
- Rules, terms, privacy information, support contact, and category controls are available.
- Real seed listings have current photos and valid pickup windows; demo content is excluded from analytics.
- Events and exchange metrics are verified against a small known dataset; backup restoration is checked.

**AI release gate:** Test matching and ambiguous Maui dates, per-item versus total budget, unknown quantities, no results, stale inventory, invented product attributes, retained damage disclosures, disabled categories, provider outage/caps, cross-user access, and instructions embedded in listing text/photos. All required invariants must pass: no unauthorized actions/private-data exposure, no fabricated listings, correct status/time exclusion, intact verification/admin review, and working manual fallback. Establish quality, latency, and cost thresholds from a baseline before rollout. Gate failures keep AI disabled; they do not stop the ordinary marketplace.

## 10. Risks, dependencies, and decisions required

| Risk | Product response | Dependency |
|---|---|---|
| Cold start / timing mismatch | Small geography, real seed inventory, visible pickup windows | Hosts and sellers with current supply |
| No-shows or stale listings | Easy closure, expiry, report flow, feedback | Seller participation and admin follow-up |
| Scam, unsafe gear, misleading photos | Prepublication review, rules, rate limits, reports | Defined policies and moderation capacity |
| Review delays consume remaining pickup time | Queue age monitoring and seller status visibility | Review staffing and response target |
| AI gives incorrect or stale advice | Ground in current records; backend eligibility checks; clarify uncertainty | Evaluation set and inventory revalidation |
| AI exposes data or follows injected instructions | Isolated permissions and minimized context | Backend access control and adversarial checks |
| AI cost or failure disrupts exchanges | Limits, disable switch, and manual fallback | Usage monitoring and operating owner |
| Unclear economics | Measure full costs and reported exchanges | Consistent cost tracking; later pricing research |

**Open decisions, prioritized before implementation:**

1. **Geography:** Confirm Kihei boundary and pickup-area taxonomy. The source inconsistently refers to “Kihei (west side)”; do not derive an island-wide or west-side service area from that wording.
2. **Nontraveler expiry:** Hosts/residents do not necessarily depart. Permit an explicit end date instead, or define a bounded relisting policy? The proposed local-seller exception needs approval.
3. **Contact model:** Choose email form/relay, reply routing, buyer verification, contact preferences, and inquiry limits.
4. **Dates:** Decide exact departure time versus date-only, week boundaries, leaving-soon threshold, recurring pickup windows, and expiry cutoff.
5. **Rules:** Finalize allowed/prohibited items, condition vocabulary, and family/sporting equipment restrictions; keep snorkel disabled until criteria exist.
6. **Moderation:** Choose automation coverage/vendor, admin review target, notification method, material-edit definition, appeal/correction handling, and reopening rules.
7. **Privacy:** Decide precise-location disclosure, retention/deletion, and who handles support and reports.
8. **Subscriptions:** Define update content and cadence; otherwise defer the opt-in.
9. **Delivery:** Assign product/engineering/operations owners, stack, launch date, operating budget, and final nonfunctional targets.

10. **AI rollout:** Select provider, data policy, usage budget, response timeout, evaluation thresholds, and operational owner. Define public assistant context and approved help sources.
11. **AI interpretation:** Confirm budget/quantity semantics and date-language defaults; ambiguous input must still be clarified.

## 11. Source traceability

| PRD subject | Business plan pages |
|---|---|
| Concept, users, Kihei focus | 1–5 |
| MVP, identity, filters, categories | 5–6 |
| Landing, results, details, listing form | 7–9 |
| Inquiry and admin screens | 10 |
| Acquisition and first-month plan | 10–15 |
| Free pilot and future promotions | 4, 16 |
| Safety, review, monitoring, alerts | 16–18 |
| Budget and success targets | 18–19 |
| Expansion and source limitations | 19–20 |

**Source file:** [MauiGearSwap.com.pdf](./MauiGearSwap.com.pdf). Source requirements are distinguished from proposed implementation decisions throughout this PRD.

**New proposal traceability:** FR-12–15 derive from the October 11 AI discussion, not the original business plan. They preserve the source's free pilot, offline payments, current-item photos, and mandatory admin approval. Related documents: [Personas](/Users/dinok/Documents/MauiGear/MauiGearSwap-Personas.md) and [User Flows](/Users/dinok/Documents/MauiGear/MauiGearSwap-User-Flows.md).
