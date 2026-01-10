# Compute and Networking

## EC2 Web/API Tier
- Example: autoscaled web nodes behind ALB, stateless services.
- Limits:
  - vCPU/instance-type quotas per region; scale limited by account quotas.
  - ENIs and IPs per instance are capped by instance type.
  - Network bandwidth depends on instance type; not line-rate on small types.

## Auto Scaling Groups
- Example: scale-out on p95 latency or queue depth.
- Limits:
  - Max instances per ASG is quota-limited; verify account limits.
  - Scale-out speed limited by instance launch times and warmup.

## Lambda for Async Jobs
- Example: image processing or webhook fanout.
- Limits:
  - Max execution time 15 minutes.
  - Memory 128 MB to 10 GB; CPU scales with memory.
  - Deployment package size 50 MB zipped/250 MB unzipped (or 10 GB container image).
  - Concurrency defaults to 1,000 per region (quota).
  - /tmp storage default 512 MB, expandable up to 10 GB.

## API Gateway
- Example: managed API front door with auth and throttling.
- Limits:
  - Payload size limit around 10 MB.
  - REST API integration timeout 29 seconds.
  - Throttle limits per stage and account; must be configured.

## VPC + NAT
- Example: private services with outbound internet via NAT.
- Limits:
  - NAT bandwidth scales with traffic but per-NAT IPs can be exhausted.
  - VPC CIDR and subnet sizes define max IPs; plan for growth.
