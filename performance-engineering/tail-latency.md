# Tail Latency

## Why It Matters
- User experience is dominated by p95/p99.
- Aggregated services amplify tail latency.

## Common Causes
- GC pauses, lock contention, noisy neighbors.
- Cache misses and slow downstreams.
- Retries that align and create spikes.

## Mitigations
- Use timeouts and budgets across calls.
- Implement hedged requests or retries with jitter.
- Isolate noisy tenants and limit concurrency.

## Senior mindset
- Monitor tail metrics continuously.
- Tail latency is often a systemic issue, not a single bug.
