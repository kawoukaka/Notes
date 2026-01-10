# Security and Observability

## IAM
- Example: role-based access for services and users.
- Limits:
  - Roles, policies, and policy document sizes are quota-limited.
  - Policy evaluation size limits can cause unexpected denies.

## KMS
- Example: encrypt/decrypt data keys for sensitive fields.
- Limits:
  - Requests per second per key are capped; high throughput needs multiple keys.
  - Key policy size is limited.

## CloudWatch Logs
- Example: centralized application logs with retention.
- Limits:
  - Log event size max 256 KB.
  - Retention max is limited (up to years); set explicit retention to control cost.

## CloudTrail
- Example: audit trail for security and compliance.
- Limits:
  - Event history retention in console is limited (typically 90 days).
  - Delivery to S3 is required for long-term retention.

## AWS WAF
- Example: protect APIs from common attacks.
- Limits:
  - Web ACLs have rule count limits.
  - Managed rule groups add to capacity usage; plan for capacity units.
