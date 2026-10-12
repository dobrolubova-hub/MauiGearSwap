# MauiGearSwap.com

**Get it free or buy it. Beach it. Pass it on.**

MauiGearSwap.com is a planned local marketplace for buying, selling, and giving away used vacation gear. Arriving travelers can find equipment near their stay, use it during their trip, and pass it on before leaving. Departing travelers, residents, and vacation rental hosts can list gear that would otherwise go unused.

The first pilot focuses on **Kihei, Maui**, with a responsive website and free listings.

## Project status

**Planning and product definition.** This repository currently contains the business plan, product requirements, personas, user flows, and instructions for development agents. Application code, a technology stack, local setup commands, and hosting configuration have not yet been established.

Features below describe planned scope, not implemented functionality. Product documents distinguish source requirements from proposals and open decisions. Personas are hypotheses to validate during the pilot.

## Why this project exists

Vacation gear is often needed for only a few days. Bringing bulky items on a flight, buying new, or renting can be inconvenient. Meanwhile, departing visitors have useful equipment they cannot easily take home.

MauiGearSwap connects that supply and demand around three practical questions:

- What gear is available near me?
- Can I pick it up within my schedule?
- Can I sell or give it away before I leave?

## Planned MVP

- Public search and browsing without an account.
- Search-first landing page and shareable results with pickup area, date, category, price, and Free-only filters.
- Listings with current actual-item photos, descriptions, condition, pickup windows, and seller deadlines.
- Verified email and secure passwordless access for sellers.
- Human admin approval before every pilot listing is published.
- Asynchronous inquiries to coordinate pickup directly.
- Seller controls for Sold, Given away, and Unavailable, plus automatic expiry.
- Listing reports, moderation records, operational monitoring, and pilot analytics.

Initial categories include permitted beach, camping, hiking, fishing, and family travel equipment. Beach chairs, umbrellas, coolers, wagons, boogie boards, and beach toys lead the initial supply effort. Snorkel gear remains disabled until hygiene and condition criteria are approved.

### Marketplace rules

Posting and arranging exchanges are free during the pilot. Buyers pay sellers directly at pickup; free items change hands without payment. The platform does not process gear payments or charge transaction fees. An inquiry does not reserve an item.

Pickup and departure times use **Maui time (`Pacific/Honolulu`)**. Only approved, available, unexpired listings appear in active search. Verification and moderation do not guarantee ownership or physical safety.

## Proposed AI assistance

The optional **Maui Gear Assistant** is a P1 enhancement with two entry points:

- **Help me find gear:** Turn natural-language needs into visible, editable filters and retrieve real eligible listings.
- **Help me list gear:** Suggest titles, categories, and descriptions from seller notes and actual-item photos, with seller review and confirmation.

A separate admin experiment may summarize review evidence and flag possible inconsistencies. Humans retain moderation decisions.

The assistant cannot autonomously send inquiries, publish listings, change prices, close items, or make moderation decisions. Ordinary search and listing forms remain usable when AI is unavailable. Provider selection, privacy handling, cost limits, and evaluation thresholds must be resolved before rollout.

## Documentation

| Document | Purpose |
|---|---|
| [Product Requirements Document](MauiGearSwap-PRD.md) | MVP scope, acceptance criteria, AI requirements, metrics, and open decisions |
| [Personas](MauiGearSwap-Personas.md) | User needs, constraints, and research hypotheses |
| [User Flows](MauiGearSwap-User-Flows.md) | Buyer, seller, admin, and assisted journeys, including failures and recovery |
| [Draft Business Plan v0.3](MauiGearSwap.com.pdf) | Original concept, pilot strategy, and business hypotheses |
| [Agent Instructions](AGENTS.md) | Shared rules for agents working on the project |
| [Claude Instructions](CLAUDE.md) | Design, development, verification, and deployment workflow for Claude |

Read the PRD first, then the personas and flows relevant to the task. The business plan's external references were not retained or reverified in its PDF export; verify those claims before using them as public evidence.

## Development approach

1. Resolve material product decisions and select a small, maintainable stack.
2. Design and implement public search, results, and listing details.
3. Add persistent listing creation, photo uploads, seller authentication, and ownership controls.
4. Build admin review, corrections, publication, closure, and expiry.
5. Add inquiry delivery, reporting, monitoring, and analytics.
6. Evaluate optional AI assistance after the core marketplace works.
7. Verify a preview release, seed real inventory, and prepare the Kihei pilot.

Update this README with actual installation, environment, development, testing, and deployment commands once those systems exist. Keep synthetic inventory clearly labeled and isolated from live listings and pilot metrics. Never commit secrets or real user contact data.

## Pilot success

The main measure is **reported completed exchanges**, including both sales and free pickups. Supporting measures include useful active inventory, repeat sellers, compatible pickup timing, publication delay, no-shows, and operating effort.

The business plan proposes first-30-day goals of 50–100 active listings, 25 reported completed exchanges, and 10 sellers listing more than one item. These are targets, not achieved results. See the PRD for definitions and additional pilot goals.

## Scope and open decisions

The initial pilot excludes native apps, platform gear payments, paid promotions, paid subscriptions, reservations, escrow, delivery, public ratings, and expansion beyond Kihei unless the project owner changes the scope.

Before implementing affected behavior, resolve service-area boundaries, end dates for local sellers, inquiry routing and buyer verification, date semantics, permitted-item rules, material-edit review policy, data retention, and deployment ownership. The PRD maintains the detailed decision list.

## Contributing

Read `AGENTS.md` before making changes. Keep work tied to PRD requirements and user flows, preserve unrelated changes, and document material assumptions. Verify the relevant successful and failure paths and describe what was checked in the change summary.

For Claude-assisted work, also read `CLAUDE.md`. Repository instructions do not authorize external outreach, purchases, or production deployment by themselves.

## License

No project license has been selected yet. Add a `LICENSE` file once the project owner decides how the code and documentation may be used.
