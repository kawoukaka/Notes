# Quickselect (Selection)

## Glossary
- Selection algorithm: find k-th order statistic without full sort. https://en.wikipedia.org/wiki/Selection_algorithm
- Median of medians: deterministic pivot with O(n) worst-case. https://en.wikipedia.org/wiki/Median_of_medians
- Partition: rearrange around a pivot. https://en.wikipedia.org/wiki/Quicksort#Partitioning

## Usage (Specific)
- Find p95 or p99 latency from an in-memory sample without sorting all values.
- Compute top-k thresholds for alerting or ranking.
- Find median for robust aggregation or anomaly detection.

## Average Time Complexity
- Average: O(n); space O(1) extra (in-place).

## Real-World Example
- NumPy uses selection for `partition` (introselect). https://github.com/numpy/numpy/blob/main/numpy/core/src/npysort/selection.c

## Tradeoffs and Failure Modes
- Average O(n), but naive pivot can degrade to O(n^2).
- Not stable; does not fully order data.
- Use median-of-medians for worst-case guarantees in adversarial inputs.

## LeetCode
- 215 Kth Largest Element in an Array
- 973 K Closest Points to Origin
- 347 Top K Frequent Elements

## Python Implementation
```python
import random

def quickselect(arr, k):
    if k < 0 or k >= len(arr):
        raise ValueError("k out of bounds")

    def partition(lo, hi):
        pivot_index = random.randint(lo, hi)
        arr[pivot_index], arr[hi] = arr[hi], arr[pivot_index]
        pivot = arr[hi]
        i = lo
        for j in range(lo, hi):
            if arr[j] <= pivot:
                arr[i], arr[j] = arr[j], arr[i]
                i += 1
        arr[i], arr[hi] = arr[hi], arr[i]
        return i

    lo, hi = 0, len(arr) - 1
    while lo <= hi:
        p = partition(lo, hi)
        if p == k:
            return arr[p]
        if p < k:
            lo = p + 1
        else:
            hi = p - 1

    return None
```
