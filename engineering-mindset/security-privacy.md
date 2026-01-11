# Security and Privacy

## Authentication and Authorization
- Use OIDC/OAuth2 for identity.
- Separate authn from authz; implement RBAC/ABAC.

## Data Protection
- Encryption in transit and at rest.
- Field-level encryption for sensitive fields.

## Threat Modeling
- Identify data flows and trust boundaries.
- Mitigate with least privilege and network segmentation.

## Real-World Examples
- Token rotation with short-lived access tokens.
- Signed URLs for temporary access to objects.
- Audit logging for admin actions.

## Senior mindset
- Secret rotation must be automatic.
- Prepare for incident response with clear playbooks.
- Privacy-by-design: minimize data collection.
