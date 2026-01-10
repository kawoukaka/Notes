# Counting Bloom Filter

## Glossary
- Counting Bloom filter: Bloom filter with counters for deletions. https://en.wikipedia.org/wiki/Bloom_filter#Counting_filters
- Counter overflow: counters saturate under heavy insertions. https://en.wikipedia.org/wiki/Bloom_filter#Counting_filters
- Deletion: decrement counters for removing items. https://en.wikipedia.org/wiki/Bloom_filter#Counting_filters

## Usage (Specific)
- TTL-based caches where entries expire or are deleted.
- Dynamic membership sets in streaming systems.
- Duplicate detection with rolling windows.

## Average Time Complexity
- Average: O(k) per insert/query/delete; space O(m * counter_size).

## Real-World Example
- RedisBloom counting filters. https://github.com/RedisBloom/RedisBloom

## Tradeoffs and Failure Modes
- Counter overflow causes false negatives or inaccurate deletions.
- Higher memory than standard Bloom filters.
- Must handle concurrent updates carefully.

## LeetCode
- N/A

## Python Implementation
```python
import mmh3

class CountingBloomFilter:
    def __init__(self, size, hash_count):
        self.size = size
        self.hash_count = hash_count
        self.counts = [0] * size

    def add(self, item):
        for i in range(self.hash_count):
            idx = mmh3.hash(item, i) % self.size
            self.counts[idx] += 1

    def remove(self, item):
        for i in range(self.hash_count):
            idx = mmh3.hash(item, i) % self.size
            if self.counts[idx] > 0:
                self.counts[idx] -= 1

    def contains(self, item):
        return all(self.counts[mmh3.hash(item, i) % self.size] > 0 for i in range(self.hash_count))
```
