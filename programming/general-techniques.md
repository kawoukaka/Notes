# Programming General Techniques (Senior Notes)

## Multithreading and Concurrency
- Choose the right model: threads, async, actors, or processes.
- Separate CPU-bound and IO-bound work.
- Control concurrency with bounded queues and semaphores.

## Locking and Synchronization
- Prefer coarse-grained locks for simplicity unless contention is proven.
- Use read-write locks for read-heavy workloads.
- Avoid holding locks across IO; risk of deadlocks.
- Use lock ordering and timeouts to prevent deadlocks.

## Lock-Free and Atomic Patterns
- Use atomic primitives for counters and flags where possible.
- Apply compare-and-swap (CAS) to avoid global locks in hot paths.
- Beware of the ABA problem; use versioning or tagged pointers.
- Prefer tested lock-free queues over custom implementations.

## Memory Models and Visibility
- Understand happens-before relationships and visibility guarantees.
- Use volatile/atomic for cross-thread visibility.
- Avoid data races; they can corrupt state even without crashes.

## Idempotency and Retries
- Make writes idempotent with request IDs.
- Use exponential backoff with jitter for retries.
- Avoid retry storms with budgets.

## Resource Management
- Apply timeouts to all external calls.
- Limit memory growth; use backpressure on queues.
- Clean up resources with context managers or try/finally.

## Error Handling
- Use structured errors with context and stable codes.
- Fail fast on invariant violations; recover on expected errors.

## Testing Discipline
- Unit tests for logic, integration for boundaries.
- Deterministic tests; avoid time-based flakiness.
- Add regression tests for concurrency and race conditions.

## Concurrency Testing
- Use stress tests with high concurrency to surface races.
- Add race detectors or sanitizers when available.
- Test timeouts and cancellation paths explicitly.
- Simulate partial failures in async workflows.

## Performance Basics
- Profile before optimizing.
- Optimize hot paths and reduce allocations.
- Measure tail latency, not just averages.
