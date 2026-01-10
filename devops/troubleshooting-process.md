# General Application Troubleshooting Process

## Triage
- Confirm impact: users affected, severity, and scope.
- Identify recent changes (deploys, config, traffic shifts).
- Stabilize first: rate limit, roll back, or fail over.

## Diagnose
- Check golden signals: latency, traffic, errors, saturation.
- Inspect logs with request IDs and correlation.
- Validate dependencies: DB, cache, network, third-party APIs.

## Mitigation
- Apply minimal safe fix to restore service.
- Communicate status and ETA.
- Collect data for root cause analysis.

## Post-Incident
- Write a blameless postmortem.
- Track action items with owners and due dates.
- Add tests or monitors to prevent recurrence.

## Failure Patterns
- Fixing symptoms without identifying root cause.
- Lack of runbooks for known failure modes.
