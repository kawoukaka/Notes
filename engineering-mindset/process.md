# System Design Process (Senior-Level)

## Thinking Process (Senior Engineer)

### 1. Ask Good Questions in Requirement Brief Meetings
- Scope: what is in/out, success criteria, and constraints (time, budget, compliance).
- Users: primary personas, top workflows, and failure tolerance.
- Data: sources, sensitivity, retention, and access patterns.
- Scale: expected QPS, growth rate, peak vs steady traffic.
- Dependencies: upstream/downstream systems, SLAs, ownership.

### 2. Connect Questions to Business Values
- Map requirements to business outcomes (revenue, cost, trust, growth).
- Ask for measurable metrics (conversion, latency SLO, cost per request).
- Identify tradeoffs in terms of impact and risk (speed vs correctness).
- Tie design choices to stakeholder priorities.

### 3. Mindset for Working Through System Design
- Start simple, then iterate with constraints and scale.
- Validate assumptions early with prototypes or benchmarks.
- Prefer clarity over novelty; operational simplicity matters.
- Treat failure modes as first-class requirements.

### 4. On-Call Readiness and Incident Response
- Consider observability early: logs, metrics, traces, runbooks.
- Identify blast radius and mitigation steps (rate limits, feature flags).
- Plan rollback paths and safe defaults.
- During incidents: stabilize, triage, communicate, then fix root cause.

### 5. Security Thinking in Design and Implementation
- Design phase: data classification, threat model, auth boundaries.
- Implementation: least privilege, secure defaults, input validation.
- Encrypt sensitive data in transit and at rest; audit access.
- Plan for secrets rotation and incident response.

### 6. Align Project Goals to Team and Org Goals
- Translate team OKRs into project milestones.
- Make tradeoffs explicit (scope, time, quality) to hit org priorities.
- Communicate risks early and seek alignment on impact.

## 1. Clarify Requirements
- Functional requirements: APIs, workflows, data model, edge cases.
- Non-functional: latency, availability, cost, data retention, privacy, compliance.
- Traffic and data growth: QPS, RPS, concurrency, payload sizes.

## 2. Define API Contracts and Data Model
- First-class entities, ownership boundaries, write/read paths.
- Idempotency and versioning from the start.

## 3. Sketch High-Level Architecture
- Core services and dependencies.
- Use a simple single-region design first, then add redundancy.

## 4. Choose Storage and Data Access Patterns
- OLTP vs OLAP needs.
- Read/write patterns: time series, point lookup, range scan.

## 5. Build for Resilience
- Stateless services with retries, timeouts, circuit breakers.
- Graceful degradation and partial availability.

## 6. Scale Strategy
- Vertical first, then horizontal.
- Sharding, caching, and async work queues.

## 7. Observability and Operations
- Metrics, traces, logs; SLOs and error budgets.
- Runbooks for common failure modes.

## 8. Security and Compliance
- Authn/authz model, data classification, audit trails.
- Least privilege, key rotation, secrets management.

## 9. Cost and FinOps
- Estimate cost drivers: storage, egress, idle compute.
- Guardrails: quotas, budgets, alerts.

## 10. Iterate and Validate
- Prototype critical paths.
- Load tests and chaos testing for real failure modes.
