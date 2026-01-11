# Distributed Systems Fundamentals

## Core Concepts
- CAP and PACELC: tradeoffs between consistency, availability, latency.
- Consensus: agree on a value despite failures (Raft/Paxos).
- Replication: leader/follower vs multi-leader; sync vs async.
- Partitioning: shard by key to scale writes and storage.
- Time and clocks: wall clock vs monotonic, clock skew, causality.

## Consistency Models
- Strong consistency for money and critical writes.
- Eventual consistency for feeds and analytics.
- Read-your-writes and monotonic reads for user experience.

## Failure Modes
- Network partitions, partial failures, split brain.
- Retry storms and cascading failures.
- Data loss from async replication lag.

## Design Practices
- Explicitly choose consistency guarantees.
- Use idempotency keys for retries.
- Implement circuit breakers and backpressure.

## Real-World Examples
- Distributed locks for leader election.
- Sharded databases with consistent hashing.
- Multi-region active-active read replicas.
