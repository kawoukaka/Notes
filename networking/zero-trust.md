# Zero Trust Networking

## Core Topics
- Verify every request; no implicit trust by network location.
- Strong identity for services and users.
- Continuous policy evaluation and logging.

## Senior mindset
- mTLS for service-to-service identity.
- Least privilege and short-lived credentials.
- Audit and monitor lateral movement attempts.

## Hands-on Commands and Examples
- `curl -v --cert client.crt --key client.key https://<host>`: test mTLS.
- `openssl s_client -connect <host>:443 -cert client.crt -key client.key`: verify mutual TLS.
- `jwt decode <token>`: inspect JWT claims (use a local tool).

## Troubleshooting Checklist
- Confirm scope: single host, AZ, region, or global.
- Validate DNS and routing first.
- Check latency, loss, and retransmits.
- Verify firewall/security group changes.
- Correlate with recent deploys or config changes.

## Example Outputs
- `ping`: packet loss and avg latency.
- `traceroute`: hops where latency spikes.
- `ss -s`: TCP state summary with retransmits.
