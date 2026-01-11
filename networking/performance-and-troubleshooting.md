# Performance and Troubleshooting

## Key Metrics
- Latency (p50/p95/p99), packet loss, retransmits, and throughput.
- Connection errors: timeouts, resets, and DNS failures.

## Troubleshooting Flow
- Verify DNS resolution and routing first.
- Check TCP handshake timing and TLS negotiation.
- Inspect saturation on network interfaces.

## Senior mindset
- Tail latency often points to network congestion or retries.
- Use packet captures sparingly; start with metrics and logs.

## Hands-on Commands and Examples
- `ss -s`: socket summary (TCP states).
- `sar -n DEV 1 5`: network interface throughput over time.
- `ethtool <iface>`: link speed and errors.
- `tcpdump -i <iface> -nn host <host>`: packet capture for debugging.

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
