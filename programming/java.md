# Java (Senior Engineer Notes)

## Concurrency and Threading
- Prefer structured concurrency via `ExecutorService` and `CompletableFuture`.
- Use bounded queues to enforce backpressure; avoid unbounded `LinkedBlockingQueue` in production.
- Distinguish CPU-bound vs IO-bound pools; size pools based on saturation goals.
- Use `ThreadLocal` sparingly; memory leaks in app servers are common.

## Memory and GC
- Understand heap regions and GC tuning; default G1 works for most services.
- Measure allocation rate; reducing churn often beats GC tuning.
- Watch for large object allocation and promotion; can cause long pauses.

## Collections and Performance
- Pick `ArrayList` over `LinkedList` for iteration.
- Use primitive collections or arrays for hot paths to avoid boxing.
- Prefer `EnumMap` and `EnumSet` for enum keys.

## I/O and Networking
- Use NIO for high-concurrency I/O; avoid blocking calls in event loops.
- Set explicit timeouts on all network operations.
- Reuse HTTP connections; configure keep-alive and connection pools.

## Error Handling
- Use checked exceptions for recoverable cases; wrap with context.
- Log with stable error codes; avoid noisy stacktraces for expected failures.
- Propagate cancellation and timeouts across layers.

## Configuration and Dependency Injection
- Use immutable config objects; validate on startup.
- Avoid runtime reflection in hot paths.
- Keep DI graph shallow to reduce startup time.

## Testing
- Prefer deterministic tests; avoid sleeping for concurrency tests.
- Use `Testcontainers` for integration; keep startup costs amortized.
- Load tests should validate tail latency, not just throughput.

## Real-World Patterns
- Circuit breaker + bulkhead to isolate flaky dependencies.
- Cache-aside with bounded caches; avoid caching nulls without TTL.
- Idempotent writes with dedupe keys for retries.
