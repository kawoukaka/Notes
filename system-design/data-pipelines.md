# Data Pipelines

## Batch vs Streaming
- Batch: cost-efficient, higher latency.
- Streaming: near real-time, complex operations.

## Common Stages
- Ingest -> validate -> enrich -> store -> serve.

## Real-World Examples
- Clickstream analytics with late-arriving events.
- ETL into warehouse for BI.
- ML feature pipelines with offline/online parity.

## Senior mindset
- Build idempotent reprocessing paths.
- Use schema registry to avoid silent breakage.
- Maintain backfill tooling for historical data.
