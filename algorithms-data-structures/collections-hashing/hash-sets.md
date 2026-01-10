# Hash Sets

## Glossary
- Set: collection of unique items. https://en.wikipedia.org/wiki/Set_(abstract_data_type)
- Hash table: underlying structure for average O(1) operations. https://en.wikipedia.org/wiki/Hash_table
- Membership test: check if element exists in set. https://en.wikipedia.org/wiki/Set_(abstract_data_type)

## Usage (Specific)
- Idempotency key tracking for write APIs (dedupe retries).
- Fast exclusion filters for streaming pipelines.
- De-duplicate event IDs in near-real-time ingest.

## Average Time Complexity
- Average: add/contains/remove O(1), resize occasionally O(n).

## Real-World Example
- Redis `SET` operations for de-duplication. https://github.com/redis/redis

## Tradeoffs and Failure Modes
- High-cardinality growth can exhaust memory; use TTL or Bloom filters.
- Hash flooding can cause worst-case behavior if keys are adversarial.
- Distributed set membership needs partitioning and consistency strategy.

## LeetCode
- 217 Contains Duplicate
- 128 Longest Consecutive Sequence
- 349 Intersection of Two Arrays

## Python Implementation
```python
class HashSet:
    def __init__(self, capacity=8):
        self.capacity = capacity
        self.size = 0
        self.keys = [None] * capacity

    def _hash(self, key):
        return hash(key) & (self.capacity - 1)

    def _resize(self):
        old_keys = self.keys
        self.capacity *= 2
        self.keys = [None] * self.capacity
        self.size = 0
        for k in old_keys:
            if k is not None:
                self.add(k)

    def add(self, key):
        if self.size * 2 >= self.capacity:
            self._resize()
        idx = self._hash(key)
        while self.keys[idx] is not None and self.keys[idx] != key:
            idx = (idx + 1) & (self.capacity - 1)
        if self.keys[idx] is None:
            self.size += 1
        self.keys[idx] = key

    def contains(self, key):
        idx = self._hash(key)
        while self.keys[idx] is not None:
            if self.keys[idx] == key:
                return True
            idx = (idx + 1) & (self.capacity - 1)
        return False
```
