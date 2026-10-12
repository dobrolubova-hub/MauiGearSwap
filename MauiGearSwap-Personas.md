# MauiGearSwap.com — Product Personas

**Version:** 0.2 | **Date:** October 11, 2026 | **Scope:** Kihei MVP pilot

## How to use these personas

These are provisional personas derived from the business plan and PRD, not interview findings. Names, scenarios, and first-person statements are illustrative. Segment definitions come from the source; motivations, behaviors, and priorities below are hypotheses to test. No demographic, income, market-share, or willingness-to-pay claims are implied.

Use these personas to evaluate search, listing, pickup coordination, and moderation decisions. Prioritize the arriving traveler and departing traveler together: the marketplace needs both sides available in the same place at compatible times. A person may move from buyer to seller during one trip; these are behavioral roles, not exclusive identities.

**Revision 0.2:** Adds AI-specific needs and validation tasks. Personas remain hypotheses; the assistant is a product capability, not an additional human persona. The core journeys remain usable without AI.

## Persona overview

| Persona | Role and priority | Main motivation | Main constraint |
|---|---|---|---|
| Alex — Arriving family organizer | Primary buyer | Get useful gear with little vacation time lost | Pickup must fit arrival and family plans |
| Jordan — Departing traveler | Primary seller / giver | Clear gear before leaving, optionally recover money | A fixed departure deadline |
| Morgan — Vacation rental host | Secondary repeat supplier and referral partner | Redistribute leftover gear and help guests | Limited operational attention |
| Casey — Local occasional lister | Secondary seller / giver | Clear unused gear through a manageable exchange | Pickup must fit everyday commitments |
| Riley — Pilot marketplace operator | Internal operational persona | Maintain current inventory and resolve problems | Small team and manual review capacity |

## 1. Alex — Arriving family organizer

**Illustrative mindset:** “I need chairs and a cooler near our condo, at a time we can actually pick them up.”

**Context:** Organizes gear for a short family stay in Kihei. May search before arrival or after discovering that the accommodation lacks needed items. Uses a phone while coordinating travel and other plans. Likely items include chairs, umbrellas, coolers, beach toys, and permitted family equipment. These behaviors are hypotheses; the source establishes families and short-stay travelers as primary users.

**Job to be done:** When preparing for or starting a Maui stay, find affordable or free gear nearby so the family can use it without transporting bulky items or spending much of the trip arranging pickup.

**Goals:**

- Know that the item is usable, still available, and close enough to collect.
- Find a pickup window that overlaps the family's schedule.
- Compare price or Free, condition, and convenience quickly.
- Understand how direct seller payment and pickup work before making contact.

**Frustrations and barriers:** Listings without dates; vague pickup areas; stale inventory; uncertain condition; waiting for a response while plans change. A free item may still be unattractive if pickup requires substantial travel or coordination. Email verification is not proof of physical safety.

**Likely journey:** Search for beach chairs → choose Kihei and a pickup date → compare photos, condition, and windows → send an inquiry with preferred pickup time → agree on meeting details → collect and pay the seller directly if applicable. Near departure, Alex may become Jordan and list the gear again.

**Product implications:**

- Support browsing without an account and clear mobile result cards (FR-01–03).
- Make pickup timing as visible as price; explain that times are Maui local time (FR-02).
- Show actual-item photos, damage disclosures, and active status (FR-03, FR-08).
- Provide a simple inquiry flow with honest delivery feedback; do not imply a reservation (FR-06).

**Success signals:** Search leads to a relevant inquiry and reported pickup; fewer failed pickups caused by mismatched timing or location. Learn whether convenience or lowest price drives the choice.

**Research questions:** What gear was missing on the last trip? When did the need become clear? How far would the person actually travel? How long can they wait for a reply before using another option?

**Usability task:** Find chairs available tomorrow near the stay, identify their condition and pickup window, and send an inquiry. Observe confusion about dates, distance, availability, and whether contact reserves the item.

**AI needs and boundaries:** Alex can describe gear, budget, pickup area, and timing in one request, then inspect editable filters and real listing links (FR-12, FR-15). Clarify total versus per-listing budget and item quantities. Do not confuse a recommended match with confirmed seller availability or a reservation. Switching to manual search preserves confirmed filters.

**AI validation task:** Ask for two chairs under a total budget tomorrow afternoon. Check whether Alex notices the exact Maui date/window, can clarify quantity, rejects an unsuitable suggestion, and recovers when AI is unavailable. Test whether assistance reduces search effort and produces relevant inquiries, rather than merely more conversation.

## 2. Jordan — Departing traveler

**Illustrative mindset:** “I'd like some money back, but the gear needs to be gone before we leave.”

**Context:** Has gear purchased or acquired for a Maui stay and cannot conveniently take it home. May only think about resale near checkout. Recovering money competes with the need for a reliable, timely handoff. Switching from sale to giveaway is a hypothesis, not a confirmed behavior.

**Job to be done:** When a trip is ending, sell or give away usable gear within the remaining pickup windows so departure is uncomplicated and the gear stays in use.

**Goals:**

- Post from a phone using current photos and a short description.
- Communicate the last feasible pickup time clearly.
- See whether a listing is pending, needs correction, or is live.
- Receive actionable inquiries and close the listing quickly after handoff.

**Frustrations and barriers:** Lengthy forms; delayed email verification or admin approval; buyers who do not show up; repetitive messages; unclear status after submission. A pending review can consume the item's remaining useful listing lifetime.

**Likely journey:** Photograph gear → enter price/Free, condition, area, pickup windows, and departure date → verify email → complete review/corrections → coordinate inquiries → mark Sold or Given away. If no exchange occurs, expiry removes the listing.

**Product implications:**

- Keep required fields understandable and preserve input after errors (FR-04).
- Make verification and review status visible, including correction reasons (FR-05, FR-08).
- Define expiry around actual availability, not a misleading all-day departure assumption (FR-07; open PRD decision).
- Make closure easy and keep Sold, Given away, and Unavailable distinct (FR-07).
- Test how price changes or switching to Free interacts with material-edit review before choosing a policy.

**Success signals:** Publication while viable pickup time remains; exchange reported before the seller deadline; seller closes accurately. Measure review delay and no-shows as well as time to exchange.

**Research questions:** When did the person decide to dispose of gear? What happened to it last time? How much effort is acceptable to recover money? When would they choose giveaway, donation, or another channel?

**Usability task:** List a cooler with two remaining pickup windows, recover from a verification issue, find its moderation status, and mark it given away. Observe whether the departure deadline and status are understood.

**AI needs and boundaries:** Jordan can request a title/category/description draft from photos and notes, but confirms all facts, price/Free, condition and damage, pickup windows, and deadline (FR-13, FR-15). Drafting must not consume the remaining listing window through an obligatory chat. Publication still requires verification and admin approval. Autonomous repricing and resale reminders are outside the first AI release.

**AI validation task:** Provide a photo and a note about a damaged cooler handle. Check that the draft preserves the defect, asks for missing timing, accepts seller corrections, and transfers to the normal form without auto-submission. Track completion time, factual corrections, and abandonment.

## 3. Morgan — Vacation rental host

**Illustrative mindset:** “Guests leave useful gear behind. I want a simple way to clear it and point incoming guests toward options.”

**Context:** A host or property manager who sometimes has leftover guest equipment and communicates with incoming visitors. Can supply listings and introduce demand through a link or QR code. Frequency, volume, and permission to dispose of specific gear require validation.

**Job to be done:** When permitted leftover gear accumulates, redistribute it with minimal staff coordination, while helping guests find nearby equipment when needed.

**Goals:**

- Manage more than one listing through secure email access.
- Arrange pickup without disrupting turnover or exposing private guest details.
- Refer guests to a straightforward, trustworthy search experience.
- Know which listings are active, closed, or awaiting review.

**Frustrations and barriers:** Reentering information; inquiries sent to the wrong staff member; pickups conflicting with property access; inventory that changes between turnovers. A mandatory departure date does not fit a permanent supplier.

**Likely journey:** Identify gear the host is authorized to list → take photos and publish individual items or a described bundle → coordinate pickup → close completed listings → share the Kihei search link with guests.

**Product implications:**

- Make multiple owned listings easy to distinguish and manage (FR-05, FR-07).
- Resolve a listing end date for nontravelers before targeting this segment heavily.
- Keep public location at an area level and arrange exact pickup privately (proposed PRD privacy model).
- Use shareable search links; partner QR materials are an acquisition activity, not a separate MVP account feature.
- Do not infer a need for bulk imports, team accounts, referral payouts, or subscriptions from this persona alone.

**Success signals:** Host publishes repeat real supply, completes exchanges, and produces guest inquiries through referrals. Track support effort per partner; do not equate a host conversation with a partnership.

**Research questions:** What happens to leftover gear today? Who can authorize listing it? Who answers inquiries? What pickup locations and hours are practical? Would supplying gear or referring guests provide more value?

**Usability task:** Manage three owned listings, identify one pending correction, and share a filtered Kihei search link with a hypothetical guest. Observe account, status, and pickup coordination friction.

**AI needs and boundaries:** Morgan may use assistance for individual drafts; it must not invent departure dates, reveal guest details, or imply authority to dispose of gear (FR-13, FR-15). Team permissions, bulk publication, and guest messaging are not introduced by the assistant.

**AI validation task:** Prepare one permitted leftover-item draft without a travel departure date; verify that the unresolved end-date policy is surfaced rather than guessed. Ask for guest contact information and verify that the public assistant cannot retrieve it.

## 4. Casey — Local occasional lister

**Illustrative mindset:** “Someone could use this gear, as long as arranging pickup doesn't become a project.”

**Context:** A resident with unused vacation or outdoor equipment. Does not have a flight deadline and may prefer either resale or giveaway. Supplies inventory outside the traveler departure cycle, but consistent supply is a hypothesis to validate.

**Job to be done:** When useful gear is no longer needed, find a nearby recipient and complete a convenient handoff without managing a complicated marketplace account.

**Goals:**

- Reach people who need the specific item.
- Set realistic pickup windows around everyday commitments.
- Choose paid or free listing clearly and disclose wear.
- Stop inquiries as soon as the item becomes unavailable.

**Frustrations and barriers:** Irrelevant inquiries; bargaining or no-shows; pressure to share a home address publicly; forced travel dates; listings remaining visible after disposal elsewhere.

**Likely journey:** List an allowed item → choose pickup windows and an approved end-date mechanism → verify and pass review → respond to an inquiry → exchange or mark unavailable if disposed of elsewhere.

**Product implications:** Clear category rules, private precise-location handling, secure listing management, and reliable closure (FR-04–05, FR-07, FR-10). Resolve local-seller expiry without weakening stale-inventory controls. Repeat listing or automated renewal should wait for evidence.

**Success signals:** Listing reaches an appropriate traveler and closes accurately with manageable seller effort. Measure abandoned forms caused by departure-date requirements and inquiries after closure.

**Research questions:** Why use this marketplace instead of existing channels? What pickup arrangements are acceptable? What causes a local seller to abandon an exchange? What listing lifetime would reflect actual availability?

**Usability task:** List an allowed hiking item without a travel departure, choose a pickup window, and mark it unavailable after giving it away through another channel. This deliberately tests the PRD's unresolved nontraveler date model.

**AI needs and boundaries:** Casey can choose manual entry or suggestions while retaining control over location disclosure, price, pickup windows, and closure (FR-13, FR-15). AI must preserve uncertainty about item details and not assume a traveler deadline.

**AI validation task:** Correct an inaccurate suggested category, disclose wear, and continue manually after a simulated outage. Check preservation of user-entered data and whether AI suggestions increase or reduce listing effort.

## 5. Riley — Pilot marketplace operator

**Illustrative mindset:** “I need to know what needs action now, without losing track of why a decision was made.”

**Context:** Internal administrator for a small pilot with manual review of every listing. May also handle support, seed inventory, and evaluate pilot results. This is an operational persona, not a customer segment.

**Job to be done:** When listings, reports, or service failures need attention, make consistent decisions quickly enough to preserve useful inventory and maintain an auditable record.

**Goals:**

- Review photos, description, condition, category, and flags in one place.
- Give sellers concrete correction or rejection reasons.
- Address urgent reports and detect stalled uploads, email, or expiry.
- Distinguish reported exchanges from unavailable items, examples, and failed inquiries.
- Understand moderation workload and actual operating cost.

**Frustrations and barriers:** Noisy alerts; unclear rules; multiple views needed for one decision; missing history; review queues containing listings whose pickup windows have already passed. Screening flags are evidence to investigate, not safety guarantees.

**Likely journey:** Review queue → inspect listing and photos → approve, hold for correction, or reject with reason → handle reports/service alerts → record resolution → review inventory and exchange metrics.

**Product implications:** Restrict admin access, maintain action history, show review age and pickup deadline, and support clear issue statuses (FR-08–10). Make alert thresholds adjustable. Establish staffing and response targets before public launch; those are operating decisions, not assumed automation capabilities.

**Success signals:** Time to publication while inventory remains viable; report-resolution time; unresolved queue size; alert usefulness; moderation effort per listing; correct lifecycle counts. Fast approval alone is insufficient if review quality suffers.

**Research questions:** Which cases need immediate action? What evidence supports each decision? What workload can one operator handle? Which notifications are useful enough to interrupt other work?

**Usability task:** Review a listing with inconsistent photos, request correction, resolve a suspected unsafe-item report, and identify a failed expiry job. Observe missing context and whether decisions remain traceable.

**AI needs and boundaries:** Riley may use evidence-linked summaries and advisory flags (FR-14) but retains every moderation decision. Public assistant sessions cannot access moderation data. A provider outage leaves manual review operational. Evaluate time saved alongside false flags, missed issues, and user correction effort.

**AI validation task:** Inspect a photo/text mismatch and a malicious instruction embedded in listing text. Verify that evidence is accessible, the operator can override a suggestion with a reason, and no automated publication or rejection occurs.

## Shared product tradeoffs

| Tension | Personas affected | Design question to test |
|---|---|---|
| Lowest price versus convenient pickup | Alex, Jordan | Does timing/location outweigh a small price difference? |
| Fast publication versus mandatory review | Jordan, Riley | Can review finish before the remaining pickup windows expire? |
| Precise location versus privacy | Alex, Morgan, Casey | Is public area information enough to decide whether to inquire? |
| Lightweight contact versus response reliability | All external personas | Is asynchronous email sufficient for time-sensitive coordination? |
| Departure-based expiry versus permanent suppliers | Morgan, Casey, Riley | Can an end-date alternative keep inventory current without confusing travelers? |

These questions guide validation; they do not authorize bypassing review or adding real-time chat, reservations, payments, or team management to the MVP.

## Pilot validation plan

**Proposed initial sample:** Interview 5 arriving travelers, 5 departing travelers, 3 hosts/managers, and 3 local listers, plus the pilot operator. Seek varied pickup constraints, paid/free experiences, and both successful and unsuccessful exchanges. This is a qualitative learning sample, not a statistically representative study. Where practical, follow the same traveler from acquisition to departure.

1. Start with recent behavior: what gear was needed, how it was acquired, where it went, and what failed. Avoid relying only on “would you use this?” answers.
2. Run the persona-specific tasks with realistic inventory and dates. Record completion, errors, confusion, and time spent coordinating.
3. Follow up after attempted pickups to compare stated preferences with outcomes. Include people who abandoned search, posting, or contact.
4. Compare interviews with search-to-contact, publication delay, reported exchange, no-show, and closure data defined in the PRD.
5. Revise or merge personas when constraints and behaviors overlap; split them only when the difference leads to a material product decision. Validate channel preferences and willingness to pay separately rather than inferring them from these profiles.

**Additional AI hypotheses:** Natural-language input improves constraint capture; listing drafts reduce effort without hiding damage; evidence summaries reduce review time without reducing quality. Test willingness to use AI and ability to recover manually, including people who decline AI. No preference for AI is assumed.

**Priority hypotheses:** Timing and proximity drive buyer selection; departure pressure makes seller simplicity important; review delay reduces viable supply; hosts can provide repeat inventory or effective referrals; local sellers need a different expiry model; email is sufficient for initial coordination. None is yet confirmed by user research.

## Source traceability

- Business plan pp. 1–5: traveler problem, families, departing visitors, residents, hosts, and short-stay use.
- Business plan pp. 5–10: search, dates, verified listing access, inquiry options, and administration.
- Business plan pp. 10–15: supply acquisition and host referral hypotheses.
- Business plan pp. 16–19: review, expiry, operational monitoring, exchange metrics, and risks.
- [Product Requirements Document](/Users/dinok/Documents/MauiGear/MauiGearSwap-PRD.md): functional requirement identifiers, proposed specifications, metric definitions, and open decisions.
- [Business plan source](/Users/dinok/Documents/MauiGear/MauiGearSwap.com.pdf): source material; no additional external research was conducted for these personas.

**Related flows:** [User Flows](/Users/dinok/Documents/MauiGear/MauiGearSwap-User-Flows.md), including manual paths and AI recovery.
