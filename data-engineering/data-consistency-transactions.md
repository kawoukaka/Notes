# Data Consistency and Transactions

## Consistency Models
- Strong consistency: critical financial or security data.
- Eventual consistency: feeds, analytics, and cache layers.
- Read-your-writes: user-facing correctness for recent actions.

## Transactions
- ACID: atomicity, consistency, isolation, durability.
- Isolation levels: read committed, repeatable read, serializable.
- Optimistic vs pessimistic concurrency control.

## Distributed Transactions
- Two-phase commit (2PC): strong guarantees with coordination cost.
- Sagas: orchestrated or choreographed compensating transactions.
- Outbox pattern: reliable event publishing with DB commits.

## Real-World Examples
- Payment flow: strong consistency with compensating refunds.
- Order processing: saga across inventory, billing, shipping.
- Event-driven systems using outbox + CDC.

## Senior mindset
- Prefer local transactions plus idempotency for scale.
- Use monotonic reads for user-facing flows.
- Document consistency guarantees in API contracts.
