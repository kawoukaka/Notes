# TCP Tuning and Connection Management

## Core Topics
- TCP handshake and slow start.
- Keep-alive and connection reuse.
- Retransmissions and congestion control.

## Senior mindset
- Tail latency often comes from retransmits or congestion.
- Tune timeouts and retry budgets together.
- Monitor SYN backlog and connection states.

## Hands-on Commands and Examples
- `sysctl net.ipv4.tcp_fin_timeout`: view TCP timeout settings.
- `sysctl net.core.somaxconn`: check listen backlog limit.
- `ss -ti dst <host>`: view TCP stats for connections to host.
- `netstat -s | grep -i retrans`: check retransmissions.

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
