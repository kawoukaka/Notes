# Performance and Troubleshooting

## Key Metrics
- Latency (p50/p95/p99), packet loss, retransmits, and throughput.
- Connection errors: timeouts, resets, and DNS failures.

## Troubleshooting Flow
- Verify DNS resolution and routing first.
- Check TCP handshake timing and TLS negotiation.
- Inspect saturation on network interfaces.

## Senior Notes
- Tail latency often points to network congestion or retries.
- Use packet captures sparingly; start with metrics and logs.
