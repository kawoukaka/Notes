# Open Addressing vs Chaining

## Glossary
- Open addressing: store entries directly in the table with probing. https://en.wikipedia.org/wiki/Open_addressing
- Separate chaining: buckets store linked lists or vectors. https://en.wikipedia.org/wiki/Hash_table#Separate_chaining
- Load factor: capacity utilization. https://en.wikipedia.org/wiki/Hash_table

## Usage (Specific)
- Open addressing for read-heavy in-memory caches with tight memory budgets.
- Chaining when frequent deletes are needed and load factor is high.
- Hybrid approaches for latency-sensitive services (e.g., Robin Hood hashing).

## Average Time Complexity
- Average: lookup/insert O(1) under moderate load; degrades near high load factors.

## Real-World Example
- Google SwissTable (open addressing). https://github.com/abseil/abseil-cpp

## Tradeoffs and Failure Modes
- Open addressing degrades rapidly near high load factors.
- Chaining has allocation overhead and pointer chasing.
- Resize costs can be large; incremental rehashing helps.

## LeetCode
- 705 Design HashSet
- 706 Design HashMap

## Python Implementation
```python
class ChainedHashMap:
    def __init__(self, capacity=8):
        self.capacity = capacity
        self.buckets = [[] for _ in range(capacity)]

    def _hash(self, key):
        return hash(key) % self.capacity

    def put(self, key, value):
        bucket = self.buckets[self._hash(key)]
        for i, (k, _) in enumerate(bucket):
            if k == key:
                bucket[i] = (key, value)
                return
        bucket.append((key, value))

    def get(self, key, default=None):
        bucket = self.buckets[self._hash(key)]
        for k, v in bucket:
            if k == key:
                return v
        return default
```
