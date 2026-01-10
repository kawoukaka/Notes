# Analytics and ML

## Athena
- Example: ad-hoc querying of S3 data lake.
- Limits:
  - Query timeout is limited (30 minutes typical).
  - Concurrent queries are quota-limited (default around 20 per account).

## Glue
- Example: ETL jobs to clean data into curated tables.
- Limits:
  - DPUs and concurrent job runs are quota-limited per account/region.
  - Job duration has a max timeout; long jobs should be split.

## Redshift
- Example: warehouse for BI dashboards.
- Limits:
  - Concurrency is limited via WLM queues; excess queries queue or fail.
  - Connection limits depend on node type; use pooling.

## SageMaker (Inference)
- Example: real-time predictions for personalization.
- Limits:
  - Payload size per inference request is limited (MBs).
  - Max concurrency is limited by instance type and endpoint config.
