# Bloom Filter

## Glossary
- Bloom filter: space-efficient probabilistic membership structure. https://en.wikipedia.org/wiki/Bloom_filter
- False positive: reports present when absent. https://en.wikipedia.org/wiki/Bloom_filter
- Hash functions: multiple hashes for bit positions. https://en.wikipedia.org/wiki/Universal_hashing

## Usage (Specific)
- Cache admission: skip caching objects likely to be one-offs.
- Pre-filter database existence checks to avoid expensive lookups.
- Edge filtering for CDN or proxy caches.

## Average Time Complexity
- Average: O(k) per insert/query where k is hash count; space O(m) bits.

## Real-World Example
- Guava BloomFilter implementation. https://github.com/google/guava

## Tradeoffs and Failure Modes
- No deletions unless using counting variant.
- False positive rate grows as filter fills; tune m and k.
- Requires stable hash functions for consistent results.

## LeetCode
- N/A (concept-heavy; rarely standalone)

## Python Implementation
```python
import mmh3

class BloomFilter:
    def __init__(self, size, hash_count):
        self.size = size
        self.hash_count = hash_count
        self.bits = [0] * size

    def add(self, item):
        for i in range(self.hash_count):
            idx = mmh3.hash(item, i) % self.size
            self.bits[idx] = 1

    def contains(self, item):
        return all(self.bits[mmh3.hash(item, i) % self.size] for i in range(self.hash_count))
```
