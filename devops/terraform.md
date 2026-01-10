# Terraform (Senior SRE Notes)

## Core Concerns
- Infrastructure as code with consistent state management.
- Least privilege for state access and providers.
- Reusability via modules and versioning.

## Practices
- Use remote state with locking.
- Keep plans and apply outputs in CI logs for auditability.
- Use workspaces or separate state for environments.

## Review and Safety
- Require code review for infra changes.
- Use policy as code for guardrails.
- Run drift detection on a schedule.

## Failure Patterns
- State corruption or missing locks.
- Hidden dependencies across modules.
- Provider version changes causing diffs.
