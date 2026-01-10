# HyperLogLog

## Glossary
- HyperLogLog: cardinality estimator using leading zeros. https://en.wikipedia.org/wiki/HyperLogLog
- Register: bucket storing max leading zeros. https://en.wikipedia.org/wiki/HyperLogLog
- Bias correction: small-cardinality adjustment. https://en.wikipedia.org/wiki/HyperLogLog

## Usage (Specific)
- Unique user counts for analytics dashboards.
- Distinct event tracking in large streams.
- Set cardinality for compliance or billing metrics.

## Average Time Complexity
- Average: O(1) per update/query; space O(m) registers.

## Real-World Example
- Redis HyperLogLog. https://github.com/redis/redis

## Tradeoffs and Failure Modes
- Estimates have error ~1.04/sqrt(m); tune m for accuracy.
- Small-cardinality bias needs correction.
- Requires good hash uniformity.

## LeetCode
- N/A

## Python Implementation
```python
import hashlib

class HyperLogLog:
    def __init__(self, p=10):
        self.p = p
        self.m = 1 << p
        self.registers = [0] * self.m

    def _hash(self, value):
        return int(hashlib.md5(value.encode("utf-8")).hexdigest(), 16)

    def _rho(self, w, max_bits):
        if w == 0:
            return max_bits + 1
        return max_bits - w.bit_length() + 1

    def add(self, value):
        x = self._hash(value)
        idx = x & (self.m - 1)
        w = x >> self.p
        max_bits = 128 - self.p
        self.registers[idx] = max(self.registers[idx], self._rho(w, max_bits))
```
