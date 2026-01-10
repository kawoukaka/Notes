# Authentication and Authorization

## AuthN vs AuthZ
- Authentication (AuthN): verify identity.
- Authorization (AuthZ): determine access to resources.
- Treat them as separate layers with explicit boundaries.

## Common Protocols and Standards
- OAuth 2.0: delegated authorization for APIs.
- OpenID Connect (OIDC): identity layer on OAuth 2.0.
- SAML 2.0: enterprise SSO, common in legacy orgs.
- JWT: self-contained tokens for stateless auth.
- mTLS: mutual TLS for service-to-service identity.

## Typical AuthN Flows
- Username/password with MFA.
- Social login (OIDC) with short-lived access tokens.
- Service accounts with client credentials.

## Typical AuthZ Models
- RBAC: roles map to permissions.
- ABAC: attributes + policies for fine-grained access.
- ReBAC: relationship-based access (graph of subjects/objects).
- Policy engines (OPA, Cedar) for centralized decision logic.

## Pain Points
- Token sprawl and long-lived credentials.
- Inconsistent permission models across services.
- Overly broad roles leading to privilege creep.
- Poor revocation strategy for JWTs.

## How to Think Through AuthN/AuthZ Issues
- Identify trust boundaries and sensitive data early.
- Define identity source of truth and token lifetimes.
- Separate authentication from authorization checks.
- Prefer least privilege; deny by default.
- Plan for revocation, rotation, and audit logging.

## Real-World Examples
- B2B SaaS with tenant-aware RBAC and per-tenant policies.
- Consumer app using OIDC and short-lived tokens with refresh.
- Internal microservices using mTLS + service account tokens.
