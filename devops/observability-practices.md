# Observability Practices (SRE)

## Core Signals
- Metrics: RED/USE for services and infrastructure.
- Logs: structured, with request IDs and trace context.
- Traces: distributed tracing across critical paths.

## Practices
- Define SLOs and alert on burn rates.
- Use dashboards for service health, not vanity metrics.
- Sample intelligently to balance cost and fidelity.

## Instrumentation
- Standardize log fields across services.
- Propagate trace IDs across boundaries.
- Capture cardinality limits to avoid metric explosions.

## Senior mindset
- Alerts should be actionable and tied to user impact.
- Observability should guide decisions, not just postmortems.
