# Cache Eviction Policies (LRU/LFU/ARC)

## Glossary
- LRU: least recently used eviction. https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU)
- LFU: least frequently used eviction. https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_frequently_used_(LFU)
- ARC: adaptive replacement cache. https://en.wikipedia.org/wiki/Adaptive_replacement_cache

## Usage (Specific)
- LRU for API response caching with strong temporal locality.
- LFU for workloads with stable hot sets (catalog lookups).
- ARC for mixed workloads where recency and frequency both matter.

## Average Time Complexity
- Average: get/put O(1) with hash map + list; LFU adds O(1) with freq lists.

## Real-World Example
- Redis LRU/LFU eviction implementation. https://github.com/redis/redis/blob/unstable/src/evict.c

## Tradeoffs and Failure Modes
- LRU can be thrashed by scans; add admission policy.
- LFU can be stale; decay counters to track recent frequency.
- ARC is more complex and harder to reason about under load.

## LeetCode
- 146 LRU Cache
- 460 LFU Cache

## Python Implementation
```python
from collections import OrderedDict

class LRUCache:
    def __init__(self, capacity):
        self.capacity = capacity
        self.cache = OrderedDict()

    def get(self, key):
        if key not in self.cache:
            return None
        self.cache.move_to_end(key)
        return self.cache[key]

    def put(self, key, value):
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value
        if len(self.cache) > self.capacity:
            self.cache.popitem(last=False)
```
