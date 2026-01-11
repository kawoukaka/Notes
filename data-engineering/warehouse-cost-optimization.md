# Warehouse Cost Optimization

## Cost Drivers
- Compute time (queries, transforms, concurrency).
- Storage growth (raw + transformed data).
- Data egress and cross-region access.

## Optimization Practices
- Partition and cluster tables to reduce scan cost.
- Use materialized views for heavy aggregations.
- Archive cold data to cheaper storage.

## Senior mindset
- Optimize for the top 20% most expensive queries.
- Enforce budgets and alerts for runaway jobs.
- Use workload management to limit concurrency spikes.
