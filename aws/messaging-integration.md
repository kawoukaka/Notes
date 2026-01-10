# Messaging and Integration

## SQS
- Example: async job queue for email, image processing, billing.
- Limits:
  - Max message size 256 KB.
  - Message retention up to 14 days.
  - Delay up to 15 minutes.

## SNS
- Example: fanout notifications to multiple subscribers.
- Limits:
  - Message size max 256 KB.
  - Delivery retries are best-effort; use DLQ for durability.

## Kinesis Data Streams
- Example: clickstream ingestion and real-time analytics.
- Limits:
  - 1 MB per record.
  - 1,000 records/sec or 1 MB/sec write per shard.
  - 2 MB/sec read per shard.
  - Retention 24 hours default (extendable to days).

## EventBridge
- Example: event bus for decoupled services.
- Limits:
  - Event size max 256 KB.
  - Throughput is quota-limited per account/region.

## Step Functions
- Example: orchestrate long-running workflows.
- Limits:
  - Standard workflow history size capped (25,000 events).
  - Execution duration can be long but cost grows per state transition.
