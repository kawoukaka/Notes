# Messaging and Streaming

## Message Queues
- Use for async work, retries, and decoupling.
- Patterns: work queue, pub/sub, delayed delivery.

## Streaming Platforms
- Use for event logs and real-time analytics.
- Patterns: log compaction, fanout, consumer groups.

## Delivery Semantics
- At-most-once: fastest, can drop.
- At-least-once: safe with idempotency.
- Exactly-once: complex; use with caution.

## Real-World Examples
- Order pipeline: validate -> charge -> fulfill -> notify.
- Fraud detection: stream events into scoring engine.
- CDC streams from DB to analytics.

## Senior mindset
- Idempotency is mandatory for at-least-once.
- Backpressure and queue depth are leading indicators.
- Use DLQs and reprocess tooling.
