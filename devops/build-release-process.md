# General Application Build and Release Process

## Build Process
- Validate inputs: correct branch, version, and dependencies.
- Compile and run unit tests; fail fast on regressions.
- Build artifact with a unique, immutable version (commit SHA).

## Release Process
- Promote artifacts across environments (dev -> staging -> prod).
- Require approvals for production releases.
- Attach release notes and change logs for traceability.

## Quality Gates
- Automated tests, lint, and security scans.
- Performance checks for critical paths.
- Rollback plans validated before release.

## Failure Patterns
- Untagged artifacts make rollback hard.
- Skipping staging leads to production-only bugs.
