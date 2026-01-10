# Monotonic Queue

## Glossary
- Monotonic queue: deque that keeps elements in sorted order. https://en.wikipedia.org/wiki/Monotonic_queue
- Sliding window min/max: maintain min/max for moving window. https://en.wikipedia.org/wiki/Sliding_window_protocol
- Amortized O(1): total cost across operations is linear. https://en.wikipedia.org/wiki/Amortized_analysis

## Usage (Specific)
- Rolling min/max for time-series dashboards.
- Windowed anomaly detection with online thresholds.
- Preprocessing for dynamic programming optimizations.

## Average Time Complexity
- Average: O(1) amortized per element; space O(k) for window size.

## Real-World Example
- Reference implementation in CP-Algorithms. https://cp-algorithms.com/data_structures/stack_queue_modification.html

## Tradeoffs and Failure Modes
- Handles only monotonic window queries; not arbitrary aggregates.
- Off-by-one errors in window eviction are common.

## LeetCode
- 239 Sliding Window Maximum
- 1438 Longest Continuous Subarray With Absolute Diff <= Limit

## Python Implementation
```python
from collections import deque

def sliding_window_max(nums, k):
    q = deque()
    result = []
    for i, val in enumerate(nums):
        while q and nums[q[-1]] <= val:
            q.pop()
        q.append(i)
        if q[0] <= i - k:
            q.popleft()
        if i >= k - 1:
            result.append(nums[q[0]])
    return result
```
