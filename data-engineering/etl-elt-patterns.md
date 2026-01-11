# ETL and ELT Patterns

## ETL
- Extract -> Transform -> Load.
- Transform data before loading into target system.
- Best for strict data quality and pre-aggregation.

## ELT
- Extract -> Load -> Transform.
- Raw data lands first, transforms run in warehouse.
- Best when warehouse compute is scalable and flexible.

## Real-World Examples
- ETL: legacy batch pipelines into a curated warehouse.
- ELT: cloud data lake with dbt transformations in warehouse.

## Senior mindset
- Choose based on latency, governance, and cost.
- ELT simplifies raw data retention but increases storage.
