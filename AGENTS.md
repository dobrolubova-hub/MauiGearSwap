# Agent instructions for MauiGearSwap

These instructions apply to work throughout this project. Follow the user's current request and higher-priority platform instructions. Use this file to guide execution, not to invent additional scope or approval requirements.

## Project purpose

Build and validate a simple marketplace for buying, selling, and giving away vacation gear in Kihei, Maui. The goal is useful local inventory and completed exchanges within travelers' pickup windows. Traffic alone does not validate the product.

The initial product is a responsive website and a free pilot. Keep implementation and operations small enough to learn before expanding.

## Read the project context

Before product or implementation work, read the relevant sections of:

- `MauiGearSwap-PRD.md`: scope, functional requirements, acceptance criteria, metrics, and open decisions.
- `MauiGearSwap-Personas.md`: user goals, constraints, journeys, and validation hypotheses.
- `MauiGearSwap-User-Flows.md`: manual and assisted journeys, confirmations, recovery, and requirement mappings.
- `MauiGearSwap.com.pdf`: original business plan, when source context is needed.

The PRD and personas are working drafts. Distinguish explicit business-plan requirements from proposed specifications and unresolved decisions. Persona names, quotes, and behaviors are illustrative hypotheses, not research findings. The source PDF's external claims are unverified; verify them before using them as factual evidence in public content.

Follow explicit user decisions made during the task. If project documents conflict, identify the conflict and resolve it using those decisions and the documents' stated decision status. Do not silently treat every PRD proposal as an approved requirement. Record meaningful product decisions in the relevant document so future agents can recover the reasoning.

## Product boundaries

- Launch in Kihei first. Do not infer a west-side or island-wide service area from inconsistent wording in the source.
- Browsing and search require no account.
- Use a search-first landing page and a separate results page. Retain queries and filters across navigation, reload, and sharing.
- Support both priced items and explicitly Free items.
- Emphasize pickup area, available pickup windows, condition, and seller deadline alongside price.
- Use current photos of the actual item. During the pilot, every listing requires email verification and admin review before publication.
- Returning sellers use secure email links or one-time codes; public seller profiles are not required.
- Gear payments happen directly between buyer and seller at pickup. The platform does not process them.
- Keep Sold, Given away, Unavailable, Expired, and moderation states distinct.
- Snorkel gear remains disabled until hygiene and condition criteria are approved. Other broad categories remain subject to item-level listing rules.
- Treat admin moderation, reports, reliable expiry, and operational visibility as core functionality.
- The PRD v0.2 proposes an optional P1 Maui Gear Assistant for search and listing drafts, plus an admin-review experiment. Keep manual paths operational; enforce tool permissions in the backend. The assistant cannot autonomously send inquiries, publish, change prices, close listings, or make moderation decisions. AI rollout requires the PRD's privacy, evaluation, cost, and recovery gates.

Do not add native apps, paid promotions, subscriptions for payment, transaction fees, escrow, reservations, real-time chat, delivery, public ratings, or geographic expansion unless the user explicitly changes the scope. Optional email updates require separate consent and are distinct from paid subscriptions. An inquiry does not reserve an item.

## Design for the users

Evaluate changes against the arriving traveler and departing traveler together: inventory is useful only when place and pickup time overlap.

- **Arriving traveler:** Can they quickly find usable gear and understand whether pickup fits their plans?
- **Departing traveler:** Can they publish while viable pickup time remains, understand review status, and close a listing easily?
- **Host or local lister:** Does the workflow work without a travel departure date? This is an open product decision; do not invent a departure date.
- **Operator:** Can they review, explain decisions, resolve reports, and detect failures without unnecessary manual work?

Keep public copy plain and concise. Do not present email verification, photo checks, or moderation as guarantees of ownership, authenticity, or physical safety. Label examples clearly and keep them out of live inventory and pilot metrics. Do not describe curated suggestions as popular without supporting data.

## Handle unresolved decisions

Review the PRD's open decisions before implementing affected behavior. Important examples include service-area boundaries, local-seller expiry, buyer verification, inquiry reply routing, exact date semantics, prohibited items, material-edit rules, moderation targets, and retention.

Resolve routine, reversible implementation details with judgment and state material assumptions. Ask a focused question when an unresolved choice materially affects scope, privacy, permissions, safety, or the user journey. Continue independent work while awaiting the answer. Avoid repeated permission requests for work the user has already authorized.

Do not choose a technology stack solely from this file. Inspect the existing project first. If the project has no implementation, recommend a small stack suited to the agreed requirements and resolve material tradeoffs before broad scaffolding.

## Engineering practices

- Inspect existing code, configuration, repository status, and local instructions before editing. Preserve unrelated user changes.
- Follow established structure and conventions. Prefer small, cohesive changes over speculative abstractions or rewrites.
- Do not introduce dependencies or services unless they solve a current requirement. Explain material costs or operational commitments.
- Validate input on the server as well as in forms. Enforce listing ownership and admin permissions on the server.
- Keep credentials and personal contact data out of public pages, source control, logs, and analytics. Use the project's secret-management mechanism.
- Protect uploads, sanitize user content, and apply configurable abuse limits to authentication, posting, and inquiries.
- Interpret pickup and departure times in `Pacific/Honolulu`; label Maui time in relevant UI. Use explicit timezone conversion rather than browser-local assumptions.
- Enforce active status and time eligibility when serving search and inquiries, even if a background expiry job is delayed.
- Persist submissions and inquiries before confirming success. Distinguish accepted inquiries from delivered email and completed exchanges.
- Make service failures recoverable, with clear status and monitoring for uploads, email, review backlogs, and expiry jobs.
- Build accessible mobile flows with labeled controls, keyboard support, visible focus, and understandable errors. Treat the PRD's accessibility and performance targets as proposals until confirmed.
- Use synthetic data for development. Do not import or expose real user data without task authorization and an appropriate handling plan.

## Verification

Use checks appropriate to the change and the established project tooling. Do not claim checks passed unless they ran successfully. Avoid tests that merely repeat implementation details.

For marketplace behavior, prioritize meaningful coverage of:

- Unverified, pending, rejected, removed, expired, sold, given-away, and unavailable listings being excluded from active search and inquiry.
- Free versus priced items, valid pickup overlap, Maui time boundaries, and seller deadlines.
- Seller ownership isolation, administrator access, and invalid or expired sign-in credentials.
- Approval, corrections, material-edit rechecks, closure, and expiry transitions.
- Failed upload or email delivery, retries, duplicate submission, and delayed background work.
- Query/filter persistence and the main buyer, seller, and administrator journeys on mobile.

Verify visible UI changes in a browser when available. Check loading, empty, error, and inactive states as well as the successful path. For documentation-only changes, check consistency, links, and whether decisions are accurately labeled; application tests are unnecessary.

## Measurement and pilot operations

Use the PRD's metric definitions. Count sales and free pickups separately; Unavailable is not a completed exchange. Offline exchanges are reported outcomes, not verified payments. Exclude demos, tests, and examples from liquidity metrics.

Measure timing friction, review delays, inquiry delivery, no-shows, repeat supply, and operating effort alongside inventory and traffic. Do not build paid services merely because a future revenue hypothesis appears in the business plan.

The source's outreach plans, advertising budgets, host pitches, and QR strategy are planning material. They do not authorize contacting people, sending messages, spending money, deploying, or publishing. Prepare reviewable work first and obtain any required authorization for the external action. Do not add approval gates to ordinary authorized local work.

## Collaboration and handoff

Give concise progress updates for substantial work. Explain material findings, decisions, and blockers in plain language. Use agents or delegation only when explicitly requested by the user or required by applicable instructions; avoid conflicting concurrent edits.

At completion, report:

- What changed and how it serves the requested outcome.
- What was verified and any checks that could not run.
- Material assumptions, unresolved decisions, or limitations.
- Links to the relevant deliverables.

Update the PRD or personas when an explicitly agreed product change makes them stale. Keep hypotheses labeled until evidence validates them. Leave the project in a state another agent can understand and continue.
