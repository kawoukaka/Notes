# Gradle and Maven (Senior SRE Notes)

## Core Concerns
- Reproducible builds with locked dependencies.
- Deterministic builds for CI reliability.
- Build caching to reduce cycle time.

## Gradle Practices
- Use the Gradle wrapper for consistent versions.
- Enable build cache and parallel execution where safe.
- Avoid dynamic dependency versions in production builds.

## Maven Practices
- Use a corporate repository proxy (Nexus/Artifactory).
- Pin plugin versions; avoid implicit defaults.
- Separate dependencyManagement from dependencies.

## Failure Patterns
- Dependency conflicts and version drift.
- Slow builds due to missing cache or excessive plugins.
- Non-reproducible artifacts across environments.
