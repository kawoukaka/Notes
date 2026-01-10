# Observability and Reliability

## Observability
- Logs: structured, with request IDs and user IDs.
- Metrics: RED/USE metrics for services.
- Traces: distributed traces for latency breakdown.

## Reliability
- SLOs and error budgets.
- Graceful degradation and feature flags.
- Load shedding when under stress.

## Real-World Examples
- Circuit breakers for flaky dependencies.
- Bulkheads for isolating failure domains.
- Retry budgets for dependency storms.

## Senior Notes
- Instrument before you scale.
- Every critical path needs dashboards and alerts.
- Keep alert noise low; use multi-signal alerts.
