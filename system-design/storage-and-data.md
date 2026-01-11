# Storage and Data

## Storage Choices
- Relational DB: transactions, strong consistency, complex queries.
- Key-value store: high throughput, simple access patterns.
- Document store: flexible schema, hierarchical data.
- Columnar store: analytics, aggregations at scale.
- Time-series DB: metrics, high ingest rate.
- Object store: large blobs, infrequent random reads.

## Data Modeling Patterns
- Normalize for write integrity; denormalize for read speed.
- Use read models/materialized views for heavy reads.
- Avoid hot partitions; shard keys must spread load.

## Consistency Tradeoffs
- Strong consistency: user-critical data and money flows.
- Eventual consistency: feeds, analytics, logs.
- Use monotonic reads for user-facing correctness.

## Indexing
- B+Tree for range queries.
- Hash indexes for point lookups.
- Partial indexes for selective filters.

## Real-World Examples
- Orders DB with append-only ledger for audit.
- Event sourcing for state reconstruction.
- CQRS for read-heavy dashboards.

## Senior mindset
- Model data lifecycles early (hot, warm, cold tiers).
- Plan for backfills and schema migrations.
- Audit fields (created_at, updated_at, version) by default.
