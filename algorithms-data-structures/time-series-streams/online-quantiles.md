# Online Quantiles (P2, t-digest)

## Glossary
- P2 algorithm: quantile estimation without storing all data. https://www.cse.wustl.edu/~jain/papers/ftp/psqr.pdf
- t-digest: clustering for accurate tail quantiles. https://arxiv.org/abs/1902.04023
- Quantile sketch: mergeable summary for distributions. https://en.wikipedia.org/wiki/Quantile

## Usage (Specific)
- p95/p99 latency in production monitoring.
- Billing based on usage percentiles.
- Tail analysis for SLO compliance.

## Average Time Complexity
- Average: O(log k) per update for t-digest; O(1) for P2; space O(k).

## Real-World Example
- Apache DataSketches quantiles. https://github.com/apache/datasketches

## Tradeoffs and Failure Modes
- Small sample sizes can under-represent tails.
- Merge operations can skew if compression factors differ.

## LeetCode
- N/A

## Python Implementation
```python
# Simplified P2-style quantile estimator for demonstration.
class P2Quantile:
    def __init__(self, q):
        self.q = q
        self.n = 0
        self.values = []

    def add(self, x):
        self.values.append(x)
        self.n += 1
        if self.n > 1000:
            self.values = sorted(self.values)[-1000:]

    def quantile(self):
        if not self.values:
            return None
        vals = sorted(self.values)
        idx = int(self.q * (len(vals) - 1))
        return vals[idx]
```
