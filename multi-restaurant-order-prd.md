# Product Requirement Document: Multi-Restaurant Single Checkout

## 1. Problem Statement
Customers currently can order only from one restaurant per order. This creates friction for groups who want different cuisines, families with varied tastes, or users ordering from nearby restaurants to save time. As a result, order frequency and basket value may be limited by the single-restaurant constraint.

## 2. Objective
Enable users to place one consolidated order containing items from multiple restaurants, with a single checkout experience, while preserving restaurant-specific operations, delivery tracking, and order fulfillment integrity.

## 3. Goals
- Increase average order value (AOV)
- Improve conversion for group orders
- Reduce app friction for mixed-menu ordering
- Increase total orders per session
- Retain operational transparency for restaurants and delivery partners

## 4. Scope

### In scope
- Multi-restaurant cart and checkout
- Restaurant-specific item grouping
- Restaurant-level payment splitting and settlement
- Delivery partner assignment and tracking per restaurant or pooled batch
- UI/UX for mixed-orders
- Notifications and receipts for each restaurant
- Handling separate preparation and dispatch times
- Support for delivery and pick-up

### Out of scope
- Ghost kitchens or sharing actual food prep across restaurants
- Cross-restaurant order modifications after placement
- Complex refund/return flows beyond standard restaurant-level processing
- Multi-restaurant loyalty program integration in phase 1

## 5. User Personas
- **Group Diner**: Friends ordering different food types for a group event
- **Family Planner**: Household ordering for family members with varying preferences
- **Office Orderer**: Team leads aggregating meals from multiple vendors
- **Busy Customer**: Wants convenience of one checkout instead of multiple orders

## 6. Key User Stories
1. As a customer, I want to add items from more than one restaurant to the same cart.
2. As a customer, I want to see each restaurant’s items clearly grouped.
3. As a customer, I want to pay once and checkout across multiple restaurants.
4. As a customer, I want to track each restaurant’s order progress separately.
5. As a customer, I want to receive separate invoices/receipts for each restaurant.
6. As an operations manager, I want delivery partners to handle split or pooled pick-ups efficiently.

## 7. Functional Requirements

### 7.1 Cart and Catalog
- Users can add items from multiple restaurants into one cart.
- Cart groups items by restaurant.
- Each restaurant group shows:
  - name, cuisine, rating
  - estimated preparation time
  - minimum order value
  - restaurant-specific offers and taxes
- Prevent adding items from closed or out-of-service restaurants to the same cart.

### 7.2 Checkout
- Single checkout page summarizing:
  - per-restaurant subtotals
  - taxes, delivery fees, packaging fees
  - consolidated total
- Display payment options and split charges architecture.
- Allow promo codes:
  - restaurant-specific promo codes apply only to relevant items
  - order-level promo codes can apply to the whole basket if supported
- Show delivery/pickup mode and estimated consolidated delivery/pickup time.

### 7.3 Pricing & Fees
- Calculate fees on a per-restaurant basis:
  - delivery
  - packaging
  - taxes
- Consolidate into a unified order total.
- Clearly itemize fees by restaurant on review screen and receipt.
- Handle cases where restaurants have different delivery partners/fee structures.

### 7.4 Order Processing
- Create one master order with multiple sub-orders or pods, each mapped to a restaurant.
- Persist restaurant-specific statuses: accepted, preparing, ready, out for delivery.
- Support restaurant-level cancellation/refund flows.
- Allow users to view both overall order status and individual restaurant sub-statuses.

### 7.5 Delivery & Logistics
- Assign delivery partner(s) based on:
  - proximity
  - restaurant readiness
  - feasibility of multi-restaurant pickup
- Options:
  - single delivery partner picks up sequentially from all restaurants
  - separate delivery partners for different restaurants if optimal
- Track delivery statuses per sub-order and aggregated.
- Estimate consolidated delivery ETA using slowest sub-order / route optimization.

### 7.6 Notifications
- Send order confirmation and status updates for:
  - the aggregated order
  - each restaurant sub-order
- Notify the user of delays or cancellations from any restaurant.
- Provide clear guidance when a sub-order is delayed but others are ready.

### 7.7 Receipts & Records
- Generate combined order summary and separate receipts for each restaurant.
- Ensure records show per-restaurant commissions and settlements for accounting.
- Email/app receipts preserve multi-restaurant breakdown.

## 8. Non-Functional Requirements
- Performance: checkout latency should remain acceptable with multiple restaurants.
- Scalability: support up to `n` restaurants per order (define based on operations, e.g., 3–4).
- Reliability: must handle partial failure gracefully (e.g., if one restaurant cancels).
- Security: preserve PCI compliance and secure payment routing.
- UX: maintain clarity and avoid cognitive overload.

## 9. User Flow
1. Customer browses restaurants.
2. Adds items from Restaurant A.
3. Adds items from Restaurant B / multiple restaurants.
4. Cart shows grouped sections.
5. User reviews grouped restaurant subtotals, fees, taxes.
6. User selects address, delivery mode.
7. User chooses payment method.
8. User checks out once.
9. System creates master order + sub-orders.
10. User tracks progress in app:
    - overall status
    - per-restaurant statuses
11. Delivery partner picks up and completes delivery.
12. Customer receives confirmation and receipts.

## 10. Acceptance Criteria
- Users can add items from at least two restaurants and proceed to unified checkout.
- Checkout displays per-restaurant fee summary and one total.
- The system can produce an order with distinct restaurant sub-orders.
- A multi-restaurant order can be tracked with separate sub-statuses.
- Partial restaurant cancellation is handled with user notification and refund calculation.
- Delivery assignment supports single or multiple delivery partners.

## 11. Metrics
- Conversion rate for multi-restaurant cart
- Average order value vs single-restaurant orders
- Cart abandonment rate for multi-restaurant carts
- Time-to-checkout for mixed orders
- Rate of multi-restaurant order cancellations
- Customer satisfaction / NPS for group ordering

## 12. Dependencies
- Restaurant catalog data and menu availability
- Delivery partner routing / assignment system
- Checkout/payment engine capable of splitting or batching charges
- Order management system that supports sub-orders
- Restaurant partner contract terms for commission settlement
- UX design and testing

## 13. Risks & Mitigations
- Risk: Complex fee presentation may confuse users.
  - Mitigation: simplify UI, highlight “single checkout, multiple restaurants”.
- Risk: Delivery delays from one restaurant affecting entire order.
  - Mitigation: surface per-restaurant ETAs, allow partial handoff tracking.
- Risk: Restaurant or item-level cancellation ruins order experience.
  - Mitigation: support easy refund, alternative suggestions, and clear communication.
- Risk: Settlement complexity for multiple vendors.
  - Mitigation: build clear sub-order accounting and use existing restaurant payout flows.

## 14. Phased Rollout

### Phase 1
- Core multi-restaurant cart
- Unified checkout
- Basic sub-order creation
- Separate status tracking
- Single delivery partner support

### Phase 2
- Delivery optimization with dynamic routing
- Advanced promo and loyalty handling
- Pick-up + delivery mixed orders
- Merchant-facing insights and reporting

### Phase 3
- Cross-restaurant combo promotions
- Multi-restaurant experience for scheduled orders
- Smart suggestions for complementary restaurants

## 15. Open Questions
- Maximum number of restaurants allowed in one order?
- Can users mix delivery and pickup restaurants in same order?
- Will all restaurant-level offers work in this flow or only selected ones?
- How will refunds be handled if only one restaurant cancels?
- Should the order appear as one transaction or multiple financial captures?

## 16. Conclusion
This feature should reduce checkout friction for group orders, increase order value, and improve customer convenience. Success depends on a smooth UI, robust order/sub-order architecture, and tight logistics coordination.
