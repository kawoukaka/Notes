# Multi-Tenancy and Geo Distribution

## Multi-Tenancy Models
- Shared tables with tenant_id.
- Schema-per-tenant for isolation.
- Cluster-per-tenant for large customers.

## Isolation Strategies
- Row-level security.
- Resource quotas per tenant.
- Noisy neighbor detection.

## Geo Distribution
- Active-active for read-heavy systems.
- Active-passive for simpler consistency.
- Data residency requirements by region.

## Real-World Examples
- SaaS with tiered resource limits.
- Multi-region read replicas for latency.
- Geo-fenced storage for compliance.

## Senior mindset
- Decide on conflict resolution early.
- Build rebalancing tools for tenant migrations.
- Test failover in each region regularly.
