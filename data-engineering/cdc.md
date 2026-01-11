# Change Data Capture (CDC)

## Core Concepts
- Capture data changes from source databases.
- Supports incremental updates and near-real-time pipelines.
- Common tools: Debezium, database logs.

## Real-World Examples
- Stream changes into analytics warehouse.
- Keep search index in sync with OLTP DB.

## Senior mindset
- Handle schema evolution explicitly.
- Monitor lag and backpressure in CDC streams.
- Ensure exactly-once or idempotent processing.
