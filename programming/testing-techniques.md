# Testing Techniques (Senior Notes)

## Test Pyramid
- Unit tests for business logic.
- Integration tests for boundaries (DB, APIs).
- End-to-end tests for critical user flows.

## Test Design
- Use equivalence classes and boundary values.
- Prefer deterministic tests; avoid time and randomness without control.
- Minimize mocks for core logic; use real dependencies when feasible.

## Concurrency and Flakiness
- Stress tests to surface race conditions.
- Use retries only for known flaky external dependencies.
- Isolate tests to avoid shared state conflicts.

## Contract and API Testing
- Define contracts for external systems.
- Use schema validation to detect breaking changes.

## Performance and Load
- Add benchmarks for critical code paths.
- Use load tests to validate tail latency and error rates.

## Senior mindset
- Tests should explain intent and failure mode.
- Prioritize coverage for high-risk paths and regressions.
