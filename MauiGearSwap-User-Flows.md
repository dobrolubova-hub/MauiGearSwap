# MauiGearSwap.com — User Flows

**Version:** 0.1 | **Date:** October 11, 2026 | **Status:** Proposed flows for the Kihei pilot

Based on [PRD v0.2](/Users/dinok/Documents/MauiGear/MauiGearSwap-PRD.md) and [Personas v0.2](/Users/dinok/Documents/MauiGear/MauiGearSwap-Personas.md). AI features are optional P1 enhancements. Core marketplace flows are P0. These flows do not resolve open product decisions by implication.

## Shared rules

- Search and browsing require no account. Seller publication requires verified email and admin approval.
- Pickup time is Maui time (`Pacific/Honolulu`). Show exact dates/windows when interpreting relative language.
- AI may search public real inventory and suggest listing text. Users perform submissions through the ordinary UI. AI never autonomously publishes, changes prices, sends messages, closes listings, or moderates.
- Current backend state controls listing eligibility, ownership, categories, price, and time overlap. Assistant output cannot override it.
- Payments and pickup arrangements remain between users. Contact does not reserve an item; assistant advice does not guarantee availability or safety.
- Preserve user-entered information and confirmed filters through recoverable failures. AI can be disabled without disabling the marketplace.
- Later inquiry drafting, resale reminders, autonomous negotiation, and booking are excluded from these first-release flows.

## UF-01 — Find gear using ordinary search

**Actor:** Alex or any visitor. **Requirements:** FR-01–03. **Entry:** Landing page or shared search URL.

1. Enter a search term and submit, or select a curated suggestion. Free gear applies Free-only.
2. Results show the term, count, and editable area/date/price/category filters. Apply backend eligibility rules.
3. Compare actual-item photos, price/Free, condition, area, pickup windows, and seller deadline.
4. Open listing details. Refresh current listing state.
5. Choose Contact seller and continue to UF-03, or return with query/filters preserved.

**Alternate paths:** Empty input stays on landing with guidance. No matches offers alternative filters; changes are user-selected. Search failure retains inputs and offers retry. An inactive detail link shows unavailable status and returns to search. Unsupported device location falls back to area selection.

**End:** A relevant detail/inquiry or an honest no-match state. **Events:** Search submitted, results returned, filters changed, listing viewed.

## UF-02 — Find gear with the Maui Gear Assistant

**Actor:** Alex. **Requirements:** FR-12, FR-15, FR-01–03. **Entry:** User selects Help me find gear.

1. Visitor describes gear, area, budget, and pickup timing.
2. Assistant identifies needed constraints and asks focused clarifications. Resolve total versus per-listing budget, quantities, and ambiguous time language without demanding a full itinerary.
3. Show interpreted, editable filters and exact Maui date/window. User can correct them or run the search.
4. Retrieve through ordinary search services; display standard result cards and normalized shareable filters. Explanations reference real listing fields and link to each item.
5. Visitor opens a listing; backend rechecks active status and time eligibility.
6. Continue through UF-03. The assistant never sends an inquiry on the user's behalf.

**Alternate paths:**

- Unknown quantity: show uncertainty; do not claim the requested quantity is satisfied.
- No matches: explain which constraints were applied, propose specific alternatives, and rerun only when the user chooses them.
- Price/time/area changes: rerun retrieval; do not reuse stale recommendations as current results.
- Outage, timeout, spending cap, disabled AI, or user preference: switch to ordinary search with confirmed filters intact. Unconfirmed language remains input to clarify, not an invented filter.
- Listing closes after recommendation: detail/inquiry shows unavailable; offer a fresh search with retained filters.

**End:** Same eligible results and inquiry route as ordinary search. **Events:** AI started, clarification required, filters applied, fallback used, listing viewed, subsequent accepted inquiry. Do not count assistant messages as seller inquiries.

## UF-03 — Contact seller and arrange pickup

**Actor:** Buyer and seller. **Requirements:** FR-06, FR-03, FR-15. **Entry:** Active listing's Contact seller button.

1. Buyer enters reply email, message, and preferred pickup window in the inquiry form.
2. Application validates input, applies abuse controls, and rechecks listing eligibility and window.
3. Buyer reviews and selects Send inquiry. This is the explicit outbound action; assisted search is not authorization to send.
4. Persist the inquiry before confirming acceptance; track notification delivery separately.
5. Seller receives listing and pickup context, then replies through the selected contact model.
6. Users agree precise location and timing and exchange directly. Payment, if any, happens at pickup.
7. Seller closes through UF-06. Optional feedback can describe failed pickup or no-show.

**Alternate paths:** Invalid fields stay editable. If eligibility changed, do not send and explain why. Delivery failure displays accurate status and uses controlled retries without duplicate inquiries. No response or no-show does not auto-close or count as an exchange. Suspicious content can be reported through UF-08.

**Open dependency:** Buyer verification and reply routing must be decided before implementation. If verification is required, it occurs before delivery and preserves the form.

**End:** Accepted/delivered inquiry or recoverable failure; an exchange is recorded only by the defined closure/feedback mechanism.

## UF-04 — Create a listing manually

**Actor:** Jordan, Morgan, or Casey. **Requirements:** FR-04–05, FR-07–08, FR-10.

1. Select List gear and enter actual-item photos, title, permitted category, description, price/Free, condition/damage, area, pickup windows, applicable deadline, contact preference, and email.
2. Validate fields and photos. Preserve input through corrections and upload retries.
3. Review details and select Submit for review. Create the account on demand for a first submission.
4. If email is unverified, save Pending verification and request verification. Verified returning sellers enter Pending review.
5. Verification completes → listing checks run → admin queue receives the item.
6. Continue through UF-07. Pending does not mean published; seller sees status and correction reasons through secure access.

**Alternate paths:** Disabled categories cannot proceed. Invalid or expired email links offer a fresh request. Local sellers do not receive a fabricated departure date: the deadline/end-date policy is a preimplementation decision. Expired pickup windows before publication require correction or nonpublication.

**End:** Pending review, correction needed, or recoverable draft/verification state. **Events:** Submission, validation errors, email verification, review entry.

## UF-05 — Prepare a listing with AI

**Actor:** Jordan, Morgan, or Casey. **Requirements:** FR-13, FR-15, FR-04–05, FR-08.

1. Choose Help me list gear and provide notes/photos under the defined data notice.
2. Assistant suggests title, permitted category, and description. It preserves disclosed wear and asks for missing facts instead of guessing brand, dimensions, safety, ownership, or deadlines.
3. Seller edits, rejects, or accepts suggestions. AI never silently overwrites manual entries.
4. Seller chooses Apply to form. Preview distinguishes suggestions from confirmed fields.
5. Seller explicitly confirms price/Free, condition/damage, pickup area/windows, and applicable deadline; complete remaining required fields.
6. Seller selects Submit for review in the normal form → UF-04 verification/checks → UF-07 admin review.

**Alternate paths:** Uncertain details remain questions or are omitted. Unsupported category is blocked. AI or image analysis fails: preserve notes/manual entries and offer manual completion. Assistance cannot waive actual photos, verification, or review. Unsaved drafts are described according to the chosen storage/retention behavior, not promised as permanently saved.

**End:** User-confirmed form submitted or retained for manual completion. **Events:** Draft generated, suggestions applied, later edited fields, fallback, submission, correction rate. No AI-generated draft is counted as a published listing.

## UF-06 — Manage, edit, and close owned listings

**Actor:** Verified seller. **Requirements:** FR-05, FR-07, FR-15.

1. Request secure email access and authenticate; application restricts access to owned listings.
2. View active/pending/closed items and select one.
3. Choose an action:
   - Edit: review changed fields and submit. Material changes return an active item to Pending review and hide it until approval.
   - Correct: address admin feedback and resubmit for review.
   - Close: select Sold, Given away, or Unavailable, review the choice, and confirm.
4. Closure immediately removes the listing from active search and disables inquiries; record reason/time.

**Alternate paths:** Invalid access links offer another request. Concurrent state changes are revalidated before committing. A closed listing cannot automatically reopen. Assistant suggestions cannot modify price or status autonomously. No-seller-response and assistant conversation are never inferred as closure.

**System expiry:** Backend hides ineligible listings at query/inquiry time, independently of the scheduled expiry job. The job records expiry under the approved deadline rules; failures alert the operator. Expired is distinct from exchange outcomes.

**End:** Correct owned listing state. Sold/Given away count as reported exchanges; Unavailable/Expired do not.

## UF-07 — Review listings with optional AI assistance

**Actor:** Riley. **Requirements:** FR-08, FR-14–15, FR-09–10.

1. Authenticate as an administrator and open pending queue with review age and pickup deadline.
2. Inspect original listing fields, photos, category rules, and automated checks.
3. If the experiment is enabled, optionally request an evidence-linked AI summary/flags. Public assistant sessions cannot access this evidence.
4. Admin inspects evidence and chooses Approve, Request correction, or Reject, recording a reason. Revalidate publication eligibility before approval.
5. Approved item becomes Active only if verification/checks are complete and pickup remains valid. Correction goes back to the seller; rejection remains unpublished.

**Alternate paths:** Suspected mismatch or uncertain authenticity requires clarification/current photo when appropriate. Operator can dismiss incorrect AI flags. An AI outage leaves manual review available. AI never automatically rejects, approves, removes, or resolves an issue. Embedded instructions in content cannot grant tool access or affect permissions.

**End:** Auditable human decision or held review. **Events:** Review outcome, reason, publication time, AI flag/override, moderation effort.

## UF-08 — Report a listing and resolve an issue

**Actor:** Visitor and Riley. **Requirements:** FR-09, FR-15.

1. Visitor selects Report listing, chooses reason, and enters explanation.
2. Persist the report and show receipt; suspected fraud/unsafe items alert admin under configured rules.
3. Admin inspects underlying listing, report, and history. Any AI summary is advisory and stays within admin access.
4. Admin records action, issue status, and resolution; remove content or request corrections when warranted.

**Alternate paths:** Failed report submission offers retry without a false receipt. AI does not promise a resolution outcome/time or disclose private moderation records to the reporting visitor. Listing status changes require an authorized admin action.

**End:** Recorded issue and human resolution. **Events:** Report category, queue age, action, resolution time.

## UF-09 — Subscribe to updates [P1, separate from AI]

**Actor:** Any visitor. **Requirements:** FR-11.

1. After update content/cadence are defined, visitor selects a separate opt-in.
2. Show the subscription description and capture consent/email.
3. Verify email before activating updates; support unsubscribe.

Posting, searching, or using AI never silently subscribes a visitor. There is no paid plan in the pilot. Failure preserves pending status and offers retry.

## Decision and verification checklist

Resolve service-area taxonomy, local-seller end dates, date-language rules, budget/quantity semantics, buyer verification/reply routing, material-edit rules, and AI data/usage limits before implementation of affected branches. A flow referencing an open decision is not approval of a default.

Verify every flow's successful, empty, invalid, unauthorized, stale-data, and service-failure states as applicable. Test AI-specific factual grounding, preserved damage disclosures, no autonomous writes, prompt injection, private-data isolation, provider limits, and manual recovery. Keep AI disabled when its release gate fails while allowing the core pilot to run.
