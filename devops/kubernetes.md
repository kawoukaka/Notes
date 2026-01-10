# Kubernetes (Senior SRE Notes)

## Core Concerns
- Declarative desired state and reconciliation loops.
- Separation of concerns: deployment vs config vs secret.
- Multi-tenant isolation via namespaces and RBAC.

## Reliability Practices
- Use readiness and liveness probes correctly.
- Set requests/limits to avoid noisy neighbor issues.
- Configure disruption budgets for critical services.

## Deployment Patterns
- Rolling updates with max surge/unavailable tuning.
- Canary or blue/green via ingress or service mesh.
- Automate rollbacks on SLO degradation.

## Observability
- Cluster-level metrics (node pressure, pod restarts).
- Service-level SLOs with alerts.

## Failure Patterns
- Resource starvation due to missing limits.
- Misconfigured probes causing restart loops.
- Overly permissive RBAC.
