# JavaScript and TypeScript (Senior Engineer Notes)

## Runtime and Concurrency
- JavaScript is single-threaded with an event loop; offload CPU-heavy work to workers.
- Use backpressure for async streams; avoid unbounded promise fanout.
- Understand microtask vs macrotask ordering to avoid starvation.

## Performance and Memory
- Avoid hidden class churn (keep object shapes stable).
- Preallocate arrays for hot loops; avoid sparse arrays for performance.
- Measure with profiling tools (Node inspector, Chrome DevTools).

## TypeScript Type System
- Use discriminated unions for complex state machines.
- Prefer `unknown` over `any` for safety.
- Keep types close to data boundaries (API clients, DB layer).

## Error Handling
- Always handle rejected promises; use centralized error boundaries.
- Normalize errors into structured objects for logging.
- Use retries with exponential backoff for transient failures.

## I/O and Networking
- Set timeouts on all requests; avoid hanging sockets.
- Reuse HTTP agents for pooling; tune keep-alive.
- Stream large payloads; avoid loading entire files into memory.

## Testing
- Prefer unit tests for logic and integration tests for IO boundaries.
- Use contract tests for external APIs.
- Test for unhandled promise rejections and race conditions.

## Real-World Patterns
- Circuit breakers around downstream services.
- Feature flags for progressive rollouts.
- Idempotency keys for write endpoints.
