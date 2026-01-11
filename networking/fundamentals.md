# Networking Fundamentals

## Core Concepts
- OSI vs TCP/IP models; know where issues map.
- TCP vs UDP tradeoffs for reliability vs latency.
- MTU and fragmentation effects on throughput.

## Senior mindset
- Design around latency and tail behavior, not just averages.
- Understand connection reuse and keep-alive tuning.
- Plan for packet loss and retries in distributed systems.

## Hands-on Commands and Examples
- `ping -c 4 <host>`: basic reachability and latency sample.
- `traceroute <host>`: hop-by-hop path to identify routing issues.
- `mtr <host>`: continuous traceroute with loss/latency stats.
- `curl -w "time_namelookup:%{time_namelookup} time_connect:%{time_connect} time_starttransfer:%{time_starttransfer}
" -o /dev/null -s <url>`: quick latency breakdown.

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
