# Storage Internals

## Core Structures
- WAL (Write-Ahead Log): durability before data files.
- LSM Trees: write-optimized structure with compaction.
- B+ Trees: read-optimized indexes for range queries.
- Bloom filters: reduce disk reads on key misses.

## Indexing and Query Planning
- Index choice drives query latency and write cost.
- Composite indexes for multi-column predicates.
- Query planner selects index based on stats and cardinality.

## Compaction and Maintenance
- LSM compaction reduces write amplification but costs IO.
- Vacuuming and pruning reclaim space.
- Reindexing improves performance after heavy churn.

## Caching and Buffering
- Buffer pools for hot pages.
- Write buffers for batching and throughput.
- Read-ahead for sequential scans.

## Failure and Recovery
- Crash recovery replays WAL.
- Replica lag impacts read freshness.
- Corruption detection via checksums.

## Real-World Examples
- RocksDB uses LSM + WAL with compaction. https://github.com/facebook/rocksdb
- Postgres uses WAL + B-Tree indexes. https://www.postgresql.org/
