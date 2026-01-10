# Load Balancing

## Types
- L4 (transport) vs L7 (application) load balancing.
- Round-robin vs least-connections vs consistent hashing.
- Global load balancing across regions.

## Senior Notes
- Consider stateful vs stateless services when choosing strategies.
- Health checks should validate dependency chains, not just process liveness.
- Session affinity can hide scaling issues; use sparingly.
