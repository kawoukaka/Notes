# Count-Min Sketch

## Glossary
- Count-Min sketch: approximate frequency estimator. https://en.wikipedia.org/wiki/Count%E2%80%93min_sketch
- Conservative update: update only minimal counters. https://en.wikipedia.org/wiki/Count%E2%80%93min_sketch
- Error bounds: overestimation by epsilon with probability delta. https://en.wikipedia.org/wiki/Count%E2%80%93min_sketch

## Usage (Specific)
- Heavy hitter detection for popular queries or endpoints.
- Approximate per-key rate limiting at high cardinality.
- Streaming analytics where full counters are too large.

## Average Time Complexity
- Average: O(k) per update/query; space O(k * w).

## Real-World Example
- Apache DataSketches (frequency sketches). https://github.com/apache/datasketches

## Tradeoffs and Failure Modes
- Overestimates counts; can inflate rare keys.
- Requires good hash functions to reduce collisions.
- Need to tune width/depth for error vs memory.

## LeetCode
- N/A

## Python Implementation
```python
import mmh3

class CountMinSketch:
    def __init__(self, width, depth):
        self.width = width
        self.depth = depth
        self.table = [[0] * width for _ in range(depth)]

    def add(self, item, count=1):
        for i in range(self.depth):
            idx = mmh3.hash(item, i) % self.width
            self.table[i][idx] += count

    def estimate(self, item):
        return min(self.table[i][mmh3.hash(item, i) % self.width] for i in range(self.depth))
```
