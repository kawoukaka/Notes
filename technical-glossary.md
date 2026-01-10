# Technical Glossary

This glossary captures technical terms used across the Notes package. It focuses on
situations, concepts, or states commonly referenced in system design and engineering.

## A
- A2A (Agent-to-Agent): coordination between specialized agents.
- ABAC: attribute-based access control.
- ARC: adaptive replacement cache.
- AuthN: authentication, verifying identity.
- AuthZ: authorization, deciding access.

## B
- Backpressure: controlling producer rate to protect consumers.
- Backfill: reprocessing historical data to populate new fields or tables.
- Blast radius: scope of impact during failure or change.
- Blue/green deploy: two environments for safe cutover.

## C
- Cache-aside: app loads cache on miss.
- Canary deploy: rollout to a small subset before full rollout.
- Circuit breaker: stop calls to failing dependency.
- CQRS: separate write and read models.
- Consistent hashing: reduce remapping on shard changes.

## D
- DAG: directed acyclic graph.
- DLQ: dead-letter queue for failed messages.
- DR: disaster recovery.
- Drift: divergence between desired and actual state.

## E
- Eventual consistency: updates propagate over time.
- Exponential backoff: increasing retry delays.

## F
- Failover: switching to standby after failure.
- Fanout: distribute events to multiple consumers.
- Feature flag: toggle functionality at runtime.

## G
- Guardrail: safety or policy constraint around behavior.

## H
- Hot partition: uneven key distribution causing overload.
- Hot path: critical, latency-sensitive code path.

## I
- Idempotency: repeated calls yield same effect.
- Index: structure for faster lookup (B-tree, hash).

## L
- Latency budget: max time allowed for a request.
- Load shedding: dropping work under overload.

## M
- MCP (Model Context Protocol): standard protocol for tools/resources for models.
- MFA: multi-factor authentication.
- Multi-tenant: shared system serving multiple customers.

## O
- OIDC: OpenID Connect identity layer.
- OLAP: analytics-oriented data access.
- OLTP: transactional data access.
- OOM: out-of-memory.

## P
- PII: personally identifiable information.
- P99: 99th percentile latency.
- Poison message: message that repeatedly fails processing.
- Principal: authenticated identity (user/service).

## R
- RAG: retrieval-augmented generation.
- RBAC: role-based access control.
- RCA: root cause analysis.
- ReBAC: relationship-based access control.
- Retry storm: cascading retries amplifying load.
- RPS/QPS: requests/queries per second.

## S
- SLO: service level objective.
- SLA: service level agreement.
- SLI: service level indicator.
- SSO: single sign-on.

## T
- Tail latency: high-percentile latency behavior.
- Thundering herd: many clients retry simultaneously.
- TTL: time to live for cached data.

## W
- Warmup: preloading caches or services before traffic.
- Watermark: stream processing boundary for late events.
