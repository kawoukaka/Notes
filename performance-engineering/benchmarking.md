# Benchmarking

## Goals
- Establish baseline performance and regression detection.
- Compare implementations fairly.

## Practices
- Control variables: hardware, data size, environment.
- Warm up to avoid cold start bias.
- Measure p50/p95/p99 and variance, not just averages.

## Senior mindset
- Synthetic benchmarks can mislead; validate with real workloads.
- Automate benchmarks in CI for critical components.
