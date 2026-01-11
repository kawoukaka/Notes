# Security and Segmentation

## Core Topics
- Network segmentation using VPCs, subnets, and security groups.
- Zero trust principles and least privilege.
- TLS termination and certificate management.

## Senior mindset
- Treat lateral movement as a primary threat model.
- Enforce egress controls and audit for exfiltration risk.
- Use mTLS for service-to-service identity where possible.

## Hands-on Commands and Examples
- `ss -tulpn`: check listeners and bound addresses.
- `iptables -L -n -v`: view firewall rules (legacy iptables).
- `nft list ruleset`: view nftables rules (modern).
- `openssl s_client -connect <host>:443`: inspect TLS certs and handshake.

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
