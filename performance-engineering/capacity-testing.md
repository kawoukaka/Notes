# Capacity Testing

## Goals
- Determine max throughput before SLOs degrade.
- Identify saturation points and scaling limits.

## Practices
- Use load tests that mimic real traffic mix.
- Ramp load gradually to observe nonlinear effects.
- Capture resource saturation metrics.

## Senior mindset
- Capacity tests should inform autoscaling policies.
- Re-run after major code or infrastructure changes.
