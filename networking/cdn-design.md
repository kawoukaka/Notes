# CDN Design

## Core Topics
- Edge caching, cache keys, and TTL strategy.
- Origin shielding and failover.
- Cache invalidation and purge workflows.

## Senior mindset
- Align cache keys with user variance and auth boundaries.
- Measure hit ratio and origin load continuously.
- Beware of thundering herd on cache miss.

## Hands-on Commands and Examples
- `curl -I <url>`: check CDN cache headers (Age, Cache-Control).
- `curl -H "Cache-Control: no-cache" -I <url>`: force revalidation.
- `dig <cdn_host>`: verify CDN CNAME and edge resolution.

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
