# Programming Language Tradeoffs (Senior Notes)

## Decision Factors
- Runtime characteristics: startup time, throughput, latency, GC behavior.
- Concurrency model: threads, async, actor model, event loop.
- Ecosystem maturity: libraries, tooling, community support.
- Team skill and hiring market.
- Deployment constraints: target platforms, memory limits, cold start.

## Common Tradeoffs
- Performance vs developer velocity.
- Static typing vs flexibility.
- Ecosystem stability vs rapid innovation.
- Simplicity vs expressiveness.

## Example Comparisons
- Java: strong ecosystem, stable runtime; heavier memory footprint.
- Python: fast iteration, rich data tooling; slower runtime, GIL limitations.
- JavaScript/TypeScript: full-stack reuse, async-first; runtime overhead and tooling complexity.

## Senior Mindset
- Start with business requirements and operational constraints.
- Consider long-term maintenance cost and observability maturity.
- Avoid over-optimizing early unless performance is a core requirement.
