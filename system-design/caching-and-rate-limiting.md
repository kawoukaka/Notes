# Caching and Rate Limiting

## Cache Layers
- Client cache: browser/local, CDN, edge KV.
- Service cache: in-process or distributed (Redis/Memcached).
- DB cache: buffer pool, materialized views.

## Cache Patterns
- Cache-aside: app manages cache; common and flexible.
- Read-through: cache loads on miss; simplify code paths.
- Write-through: writes go to cache and store; predictable but can be slower.
- Write-behind: async to store; improves write latency, risks loss.

## Cache Key Design
- Include versioning for schema changes.
- Normalize inputs (case, locale, default filters).
- Avoid high-cardinality keys without TTL.

## Cache Invalidation
- TTL-based: simplest; use jitter to avoid thundering herd.
- Event-driven: invalidate on writes.
- Hybrid: TTL + event invalidation for correctness.

## Rate Limiting Patterns
- Token bucket: smooth bursts.
- Leaky bucket: strict steady flow.
- Sliding window log: precise but heavy.
- Sliding window counter: approximate and efficient.

## Real-World Examples
- API gateway limits per key + IP (token bucket).
- Abuse prevention with tiered limits (free vs paid).
- Database protection by limiting expensive queries.

## Senior mindset
- Keep rate limit state close to edge for low latency.
- Use consistent hashing for counters to reduce cross-node chatter.
- Use idempotency keys to avoid repeated heavy operations.
