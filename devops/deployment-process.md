# General Application Deployment Process

## Deployment Steps
- Pre-checks: config validation, dependency health, capacity.
- Deploy with a safe strategy (rolling, canary, blue/green).
- Post-checks: health checks, key metrics, error rates.

## Rollback Strategy
- Automated rollback when SLOs degrade.
- Keep previous versions hot for quick revert.
- Ensure data migrations are backward compatible.

## Communication
- Announce deployments with impact and rollback plan.
- Provide status updates during deployment windows.

## Failure Patterns
- Config drift between environments.
- Incompatible schema changes without rollback path.
