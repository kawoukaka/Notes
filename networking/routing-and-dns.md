# Routing and DNS

## Routing
- Static vs dynamic routing; route propagation matters in multi-region.
- BGP is the backbone of internet routing; understand failure modes.
- NAT and SNAT implications on source identity.

## DNS
- TTL settings balance freshness vs cache load.
- Split-horizon DNS for internal vs external views.
- Understand CNAME vs A/AAAA implications.

## Senior Notes
- DNS is often the hidden root cause; always check resolution paths.
- Use health-checked DNS for failover but test propagation delays.
