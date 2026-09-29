# Zomato Multiorder — Execution Plan

## What We're Building

Three interconnected capabilities that need to ship in sequence (each one depends on the previous):

1. **Multi-Restaurant Cart (P0)** — Let users add food items from multiple nearby restaurants into one unified cart
2. **Single Checkout (P1)** — One payment flow that covers all restaurants, with clear fee breakdowns
3. **Coordinated Delivery (P2)** — Unified tracking screen showing parallel delivery status for all legs

These aren't three separate features — they're one experience built in phases. You can't do single checkout without a multi-restaurant cart, and coordinated delivery doesn't make sense without unified checkout.

---

## Goals and Non-Goals

### Goals
- Increase average order value by reducing the friction of "settling for one restaurant"
- Improve conversion for group and multi-person orders
- Reduce drop-off when customers want items from more than one place
- Increase orders per session
- Maintain clear operational visibility for restaurants and delivery partners throughout

### Non-Goals (equally important to define)
- **Not replacing** the existing single-restaurant flow — this is additive, not a rewrite
- **Not enabling** orders from restaurants outside the supported delivery radius
- **Not redesigning** how restaurants receive and manage orders on their end
- **Not building** a social/group-chat ordering experience
- **Not touching** restaurant discovery or recommendation algorithms

I want to be clear about non-goals because scope creep is the biggest risk here. This feature is already complex enough without pulling in adjacent problems.

---

## RICE Prioritization

I used a RICE-inspired framework to sequence the three solutions. The prioritization follows product dependency — you literally can't build P1 without P0.

| Opportunity | Reach | Impact | Confidence | Effort | Priority |
|---|---|---|---|---|---|
| Multi-Restaurant Cart — Unified cart across nearby restaurants | HIGH | MED | HIGH | HIGH | **P0** |
| Single Checkout — One payment for all restaurants | MED | HIGH | MED | MED | **P1** |
| Coordinated Delivery — Unified tracking and delivery coordination | MED | MED | HIGH | MED | **P2** |

**Why this sequence matters:**
- P0 has the highest reach because it changes the most visible part of the experience (browsing and carting)
- P1 has the highest impact per user because it eliminates duplicate payments and fee confusion
- P2 is the polish layer — it makes the experience feel complete but the feature is usable without it

---

## Phased Rollout

### Phase 1 — Multi-Restaurant Cart (P0) · ~8–10 weeks

**What ships:**
- "Multiorder Eligible" badges on restaurants within 300-400m of each other
- Ability to add items from a second (and third) restaurant to the same cart
- Cart view showing items grouped by restaurant with per-restaurant subtotals
- "Nearby Multiorder Hubs" — curated restaurant pairings based on proximity and category

**User-facing behavior:**
- User taps "Multiorder" tab or sees eligible restaurants on home screen
- Selects Restaurant A, adds items → gets prompted with nearby Restaurant B options
- Cart shows both restaurants' items, grouped and clearly separated
- "Continue to Checkout" is disabled until at least 2 restaurants have items (for multiorder flow)

**What we're NOT doing in Phase 1:**
- No unified payment — user still goes through existing checkout per restaurant
- No delivery coordination — orders are dispatched independently
- No combined delivery fee discount yet

### Phase 2 — Single Checkout (P1) · ~6–8 weeks after P0

**What ships:**
- Unified bill summary showing per-restaurant costs, combined delivery fee, platform fees, and taxes
- Bundled delivery fee with visible savings ("₹35 instead of ₹70 — you save ₹35!")
- Single payment flow — one UPI/card transaction covers all restaurants
- Partial failure handling — if one restaurant rejects, the other order proceeds + instant refund

**Key design decisions:**
- Fee transparency is non-negotiable. Every line item must show which restaurant it belongs to
- Payment failure for one restaurant should NOT cancel the entire order
- Cancellation is available per-restaurant until kitchen starts prep

### Phase 3 — Coordinated Delivery (P2) · ~6–8 weeks after P1

**What ships:**
- Single delivery partner assigned for multi-stop pickup (restaurants within proximity threshold)
- Unified tracking map showing pickup progress across restaurants
- Parallel status timeline: "Restaurant A: Preparing → Picked Up" / "Restaurant B: Ready → Waiting for pickup"
- Combined ETA with individual restaurant prep time visibility

**Operational complexity (honest assessment):**
- This phase depends heavily on ops and logistics, not just product/eng
- Delivery partner routing needs to account for prep time differences between restaurants
- Cold-chain concerns: biryani + ice cream in same bag needs thermal isolation (dual-cavity bags)

---

## Functional Requirements & Acceptance Criteria

### Cart (P0)
- Users can add items from 2–3 eligible restaurants in one session
- Cart updates (add, remove, modify) complete within 2 seconds
- If a restaurant goes offline or an item becomes unavailable mid-session, the user gets a clear notification without losing their other restaurant items
- "Multiorder Eligible" badge only appears for restaurants within the proximity threshold

### Checkout (P1)
- Checkout displays: item costs per restaurant, combined delivery fee, individual platform fees, applicable taxes, total payable
- Single payment transaction with existing payment methods (UPI, cards, wallets)
- If payment fails, retry flow covers all restaurants — no partial payment states
- If one restaurant declines the order post-payment, that portion is auto-refunded within 5 minutes

### Delivery (P2)
- One delivery partner handles multi-stop pickup when restaurants are within 400m
- Tracking screen shows individual prep status per restaurant + combined delivery ETA
- If one restaurant is significantly delayed, the system can decide to dispatch the ready order first (configurable threshold)

---

## Non-Functional Requirements (PQRSTU)

I use a PQRSTU framework to make sure I'm not just thinking about features:

| Dimension | Requirement |
|---|---|
| **P — Performance** | Cart updates < 2s. Checkout load < 3s. Tracking updates every 30s |
| **Q — Quality** | Checkout must clearly display all cost components — no hidden fees |
| **R — Reliability** | Multiorder must recover gracefully from partial restaurant or payment failures |
| **S — Security** | Uses Zomato's existing secure payment infra. No new payment data stored |
| **T — Transparency** | Each restaurant shows price, availability, ratings, and applicable fees |
| **U — Usability** | Complete a multiorder in ≤ 3 additional taps vs. a single order |

---

## Success Metrics

### North Star
**Increase in orders per eligible ordering user** — not just "more orders" broadly, but specifically more orders from users who have access to the multiorder feature.

### L1 Metrics (leading indicators)
| Metric | What It Tells Us |
|---|---|
| Multiorder adoption rate | Are users discovering and trying the feature? |
| Orders per user (multiorder cohort) | Are they ordering more when they can combine? |
| Average order value (AOV) | Is the combined cart actually bigger? |

### Counter Metrics (guardrails — these should NOT move negatively)
| Metric | Guardrail |
|---|---|
| Single-order conversion rate | Should not decrease — we're not cannibalizing existing behavior |
| Average delivery time | Should not increase — coordinated delivery shouldn't slow things down |
| Restaurant order acceptance rate | Should not decline — restaurants shouldn't reject more orders |
| Delivery partner utilization | Should remain within operational capacity |

If any counter metric moves by more than 5% in the wrong direction during rollout, that's a red flag worth pausing for.

---

## Risks I'm Watching

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| Delivery partners overwhelmed by multi-stop routes | Medium | High | Start with restaurants < 300m apart; single-valet model |
| Restaurant prep time mismatch (one ready, one delayed) | High | Medium | Show individual prep ETAs; allow partial dispatch |
| User confusion — "is this one order or two?" | Medium | Medium | Clear UI separation per restaurant in cart + tracking |
| Payment partial failure edge cases | Low | High | Auto-refund within 5 min; no partial payment states |
| Feature cannibalization of single orders | Low | Medium | Monitor counter metrics; A/B test before full rollout |

---

## Go-to-Market

### Rollout Strategy
1. **Internal dogfood** — Zomato employees in Bangalore for 2 weeks
2. **City beta** — Indiranagar, Bangalore (high-density restaurant area, tech-savvy users)
3. **Expanded beta** — Top 5 multiorder-eligible zones across Bangalore, Mumbai, Delhi
4. **GA** — All supported cities where restaurant proximity threshold is met

### Feature Discovery
- Home screen banner: "Craving different things? Order from multiple restaurants together!"
- "Multiorder" tab in bottom navigation
- Category chips: filter by "Multiorder Eligible"
- Push notification to existing power users (3+ orders/week)

---

## Prototype Reference

I prototyped both mobile and web experiences using Google Stitch. The screens cover the full flow:

**Mobile (7 screens):** Home discovery → Intro sheet → Restaurant selection → Menu browsing → Multi-restaurant cart → Single checkout → Coordinated tracking

**Web (5 screens):** Home discovery → Restaurant discovery → Menu with multiorder active → Single checkout → Coordinated tracking

See the full interactive prototype: [Prototype Showcase](docs/prototype-showcase.html)

![Product Solution Overview](assets/screenshots/product-solution.png)

---

*Back to [README](README.md) · Product context in [context.md](context.md)*
