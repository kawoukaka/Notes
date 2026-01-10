# Python (Senior Engineer Notes)

## Concurrency Model
- GIL limits CPU-bound threads; use multiprocessing or native extensions.
- For I/O, use `asyncio` with bounded semaphores to cap concurrency.
- Avoid mixing blocking calls in async loops; isolate in thread pools.

## Performance
- Profile before optimizing; `cProfile` and `py-spy` are common.
- Reduce object allocations in tight loops; prefer local variables.
- Use `list`/`dict` comprehensions judiciously; readability first.

## Data Structures
- `dict` and `set` are highly optimized; use them for membership checks.
- `collections.deque` for queues; list pops from left are O(n).
- `array` or `numpy` for numeric workloads.

## I/O and Networking
- Use timeouts everywhere; requests without timeouts are production bugs.
- Reuse HTTP sessions for pooling.
- For large files, stream reads/writes to avoid memory spikes.

## Error Handling
- Prefer explicit exceptions; avoid bare `except`.
- Keep stack traces for unexpected failures; add context for expected failures.
- Use structured logging with request IDs.

## Dependency and Packaging
- Pin dependencies; maintain a lockfile.
- Separate runtime vs dev dependencies.
- Use virtual envs and keep base images slim.

## Testing
- Use `pytest` with fixtures; keep fixtures small and layered.
- Use `freezegun` or time-mocking for deterministic time-based tests.
- Add contract tests around external APIs.

## Real-World Patterns
- Use background workers (Celery/RQ) for long tasks.
- Add circuit breakers for flaky dependencies.
- Build idempotency into write endpoints.
