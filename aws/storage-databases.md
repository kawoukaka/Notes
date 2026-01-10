# Storage and Databases

## S3 Data Lake
- Example: raw events stored in S3, processed by Athena/Glue.
- Limits:
  - Object size up to 5 TB; single PUT up to 5 GB.
  - Multipart upload requires parts (up to 10,000 parts).
  - Buckets per account are limited (default 100).

## EBS for Stateful EC2
- Example: database volumes or log storage.
- Limits:
  - IOPS and throughput are capped per volume type and size.
  - Max volume size depends on type; plan for growth.

## RDS (MySQL/Postgres)
- Example: transactional store for user data.
- Limits:
  - Storage max varies by engine/instance; Aurora supports very large storage (up to 128 TB).
  - Connection limits per instance; use pooling.
  - Read replicas are limited per engine.

## DynamoDB
- Example: user sessions or high-throughput key-value data.
- Limits:
  - Item size max 400 KB.
  - Query/scan returns up to 1 MB per page.
  - Partition throughput is capped; hot keys throttle.

## ElastiCache (Redis)
- Example: shared cache or short-lived session store.
- Limits:
  - Max memory per node type; cluster size is quota-limited.
  - Redis value size max 512 MB.

## OpenSearch
- Example: search and log analytics.
- Limits:
  - Shards per node are limited; oversharding kills performance.
  - Recommended shard size ~10-50 GB for stability.
