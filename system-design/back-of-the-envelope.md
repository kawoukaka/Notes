# Back-of-the-Envelope Estimation

## Goals
- Size systems quickly to validate feasibility.
- Identify dominant cost and capacity drivers.
- Sanity-check architecture choices.

## Common Estimations
- QPS = DAU * actions per user / seconds per day.
- Storage = events per day * bytes per event * retention.
- Bandwidth = QPS * response size.
- Cache size = hot key count * entry size.

## Latency Budgeting
- Set target p95/p99 latency.
- Allocate budget across hops (API, DB, cache).

## Throughput and Concurrency
- Concurrency = QPS * average latency.
- Thread pool sizing based on IO vs CPU bounds.

## Cost Drivers
- Egress bandwidth, storage, and idle compute.
- Reads vs writes in managed databases.

## Senior mindset
- Use ranges, not precise numbers.
- Validate with real traffic where possible.
- Revisit estimates after instrumentation.
