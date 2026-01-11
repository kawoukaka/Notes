# Lakehouse Architecture

## Core Ideas
- Combine data lake flexibility with warehouse reliability.
- Use open table formats (Delta, Iceberg, Hudi).
- Support batch and streaming on the same storage.

## Design Considerations
- Partitioning strategy for performance and cost.
- Schema evolution and enforcement.
- Storage tiering (hot/warm/cold).

## Real-World Examples
- Unified analytics for BI + ML feature pipelines.
- Near-real-time dashboards with incremental updates.

## Senior mindset
- Optimize for query patterns; over-partitioning hurts.
- Plan for compaction and file layout maintenance.
