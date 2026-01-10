# Hash Maps (Dictionary)

## Glossary
- Hash function: maps keys to bucket indices. https://en.wikipedia.org/wiki/Hash_function
- Load factor: ratio of entries to buckets. https://en.wikipedia.org/wiki/Hash_table
- Robin Hood hashing: balancing probe lengths. https://en.wikipedia.org/wiki/Robin_Hood_hashing

## Usage (Specific)
- Join-style lookups in ETL (keyed enrichments by user_id or session_id).
- Per-request memoization for expensive calculations.
- Real-time aggregation counters (event-type, status, region buckets).

## Average Time Complexity
- Average: get/put/delete O(1), resize occasionally O(n).

## Real-World Example
- Abseil `flat_hash_map` (open addressing, cache-friendly). https://github.com/abseil/abseil-cpp

## Tradeoffs and Failure Modes
- Unbounded cardinality leads to memory blowups; enforce TTL or caps.
- Poor hash distribution causes clustering and latency spikes.
- Resizing under load can cause tail latency; use incremental rehashing if possible.

## LeetCode
- 1 Two Sum
- 560 Subarray Sum Equals K
- 128 Longest Consecutive Sequence

## Python Implementation
```python
class HashMap:
    def __init__(self, capacity=8):
        self.capacity = capacity
        self.size = 0
        self.keys = [None] * capacity
        self.values = [None] * capacity

    def _hash(self, key):
        return hash(key) & (self.capacity - 1)

    def _resize(self):
        old_keys, old_values = self.keys, self.values
        self.capacity *= 2
        self.keys = [None] * self.capacity
        self.values = [None] * self.capacity
        self.size = 0
        for k, v in zip(old_keys, old_values):
            if k is not None:
                self.put(k, v)

    def put(self, key, value):
        if self.size * 2 >= self.capacity:
            self._resize()
        idx = self._hash(key)
        while self.keys[idx] is not None and self.keys[idx] != key:
            idx = (idx + 1) & (self.capacity - 1)
        if self.keys[idx] is None:
            self.size += 1
        self.keys[idx] = key
        self.values[idx] = value

    def get(self, key, default=None):
        idx = self._hash(key)
        while self.keys[idx] is not None:
            if self.keys[idx] == key:
                return self.values[idx]
            idx = (idx + 1) & (self.capacity - 1)
        return default
```
