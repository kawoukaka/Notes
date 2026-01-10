# Docker (Senior SRE Notes)

## Core Concerns
- Image size and layering: reduce attack surface and pull time.
- Immutable artifacts: build once, run anywhere; avoid runtime mutation.
- Reproducibility: pin base images and dependencies.

## Build Practices
- Multi-stage builds to separate build and runtime layers.
- Use `.dockerignore` to avoid context bloat.
- Tag by git SHA and semantic version for traceability.

## Runtime Practices
- Run as non-root; drop capabilities where possible.
- Configure resource limits (CPU/memory) and health checks.
- Use read-only filesystems when feasible.

## Observability
- Emit logs to stdout/stderr for aggregation.
- Expose metrics endpoints for liveness and readiness.

## Failure Patterns
- OOM due to missing limits or memory leaks.
- Slow cold starts due to huge images.
- Hidden dependency on mutable filesystem.
