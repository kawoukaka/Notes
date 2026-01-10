# Cuckoo Filter

## Glossary
- Cuckoo filter: compact membership structure with deletions. https://en.wikipedia.org/wiki/Cuckoo_filter
- Fingerprint: small hash stored in bucket. https://en.wikipedia.org/wiki/Cuckoo_filter
- Cuckoo hashing: relocate items on insert collisions. https://en.wikipedia.org/wiki/Cuckoo_hashing

## Usage (Specific)
- Edge caches to avoid repeated misses with deletions.
- Client-side filtering for sync and replication systems.
- Membership checks when Bloom false positives are too high.

## Average Time Complexity
- Average: O(1) insert/query/delete; inserts may trigger short relocation loops.

## Real-World Example
- Cuckoo Filter reference implementation. https://github.com/efficient/cuckoofilter

## Tradeoffs and Failure Modes
- Inserts can fail when table is near capacity.
- Fingerprint collisions can raise false positives.
- Requires careful tuning of bucket size and max kicks.

## LeetCode
- N/A

## Python Implementation
```python
import mmh3
import random

class CuckooFilter:
    def __init__(self, buckets=1024, bucket_size=4, max_kicks=200):
        self.buckets = buckets
        self.bucket_size = bucket_size
        self.max_kicks = max_kicks
        self.table = [[] for _ in range(buckets)]

    def _fingerprint(self, item):
        return mmh3.hash(item) & 0xFFFF

    def _index(self, item):
        return mmh3.hash(item) % self.buckets

    def _alt_index(self, idx, fp):
        return (idx ^ mmh3.hash(str(fp))) % self.buckets

    def add(self, item):
        fp = self._fingerprint(item)
        i1 = self._index(item)
        i2 = self._alt_index(i1, fp)
        if len(self.table[i1]) < self.bucket_size:
            self.table[i1].append(fp)
            return True
        if len(self.table[i2]) < self.bucket_size:
            self.table[i2].append(fp)
            return True
        idx = i1 if random.random() < 0.5 else i2
        for _ in range(self.max_kicks):
            j = random.randrange(len(self.table[idx]))
            fp, self.table[idx][j] = self.table[idx][j], fp
            idx = self._alt_index(idx, fp)
            if len(self.table[idx]) < self.bucket_size:
                self.table[idx].append(fp)
                return True
        return False

    def contains(self, item):
        fp = self._fingerprint(item)
        i1 = self._index(item)
        i2 = self._alt_index(i1, fp)
        return fp in self.table[i1] or fp in self.table[i2]

    def remove(self, item):
        fp = self._fingerprint(item)
        i1 = self._index(item)
        i2 = self._alt_index(i1, fp)
        if fp in self.table[i1]:
            self.table[i1].remove(fp)
            return True
        if fp in self.table[i2]:
            self.table[i2].remove(fp)
            return True
        return False
```
