# Consistent Hashing

## Glossary
- Consistent hashing: minimize remaps on node changes. https://en.wikipedia.org/wiki/Consistent_hashing
- Virtual nodes: multiple positions per node to reduce skew. https://en.wikipedia.org/wiki/Consistent_hashing#Virtual_nodes
- Ring: hash space represented as a circle. https://en.wikipedia.org/wiki/Consistent_hashing

## Usage (Specific)
- Cache clusters (Redis/Memcached) to reduce rebalancing on node churn.
- Sharded databases or queues with minimal redistribution.
- Client-side load distribution for edge caches.

## Average Time Complexity
- Average: O(log v) lookup with sorted ring of v virtual nodes.

## Real-World Example
- Ketama consistent hashing used by libmemcached. https://github.com/awesomized/libmemcached/blob/master/libmemcached/ketama.c

## Tradeoffs and Failure Modes
- Hot keys still create hotspots; virtual nodes help but do not solve.
- Requires monitoring for uneven distribution.
- Rebalancing can cause cache misses; consider warmup.

## LeetCode
- N/A (common system design concept, rarely standalone)

## Python Implementation
```python
import bisect
import hashlib

class ConsistentHashRing:
    def __init__(self, nodes=None, replicas=100):
        self.replicas = replicas
        self.ring = []
        self.nodes = {}
        if nodes:
            for node in nodes:
                self.add(node)

    def _hash(self, key):
        return int(hashlib.md5(key.encode("utf-8")).hexdigest(), 16)

    def add(self, node):
        for i in range(self.replicas):
            h = self._hash(f"{node}-{i}")
            self.ring.insert(bisect.bisect(self.ring, h), h)
            self.nodes[h] = node

    def get(self, key):
        if not self.ring:
            return None
        h = self._hash(key)
        idx = bisect.bisect(self.ring, h) % len(self.ring)
        return self.nodes[self.ring[idx]]
```
