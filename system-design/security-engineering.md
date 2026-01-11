# Security Engineering (Deep Dive)

## Threat Modeling
- Identify assets, trust boundaries, and attacker goals.
- Use STRIDE or similar frameworks to enumerate threats.
- Prioritize mitigations by impact and likelihood.

## Secure SDLC
- Security requirements in design reviews.
- Static analysis and dependency scanning in CI.
- Pre-deploy security checks and approvals.

## Secrets Management
- Centralized secret storage with rotation.
- Least privilege for secret access.
- Avoid secrets in code, logs, or client-side storage.

## Data Protection
- Encrypt in transit and at rest.
- Field-level encryption for sensitive attributes.
- Tokenization or anonymization where possible.

## Access Control
- Enforce least privilege with RBAC/ABAC.
- Strong authentication and MFA for privileged access.
- Audit logs for sensitive operations.

## Incident Response
- Playbooks for common incidents.
- Rapid containment and forensic preservation.
- Post-incident fixes and risk reduction.

## Real-World Examples
- API gateways enforcing WAF and rate limits.
- Rotating database credentials with short TTLs.
- Data loss prevention for outbound traffic.
