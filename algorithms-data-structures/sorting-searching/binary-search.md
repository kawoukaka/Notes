# Binary Search

## Glossary
- Lower bound: first position where value could be inserted. https://en.wikipedia.org/wiki/Binary_search_algorithm
- Upper bound: first position after the last occurrence. https://en.wikipedia.org/wiki/Binary_search_algorithm
- Monotonic predicate: a boolean condition that flips once. https://en.wikipedia.org/wiki/Monotonic_function

## Usage (Specific)
- Boundary search in monotonic systems (first failing build, minimum capacity).
- Feature flag rollout thresholds (find last stable version).
- Time-based queries in sorted event logs (first event after T).

## Average Time Complexity
- Average: O(log n); space O(1).

## Real-World Example
- C++ `lower_bound` implementation in libc++. https://github.com/llvm/llvm-project/blob/main/libcxx/include/__algorithm/lower_bound.h

## Tradeoffs and Failure Modes
- Off-by-one errors are common; keep a strict invariant.
- Requires sorted data or a monotonic predicate.
- Use iterative form to avoid recursion overhead.

## LeetCode
- 704 Binary Search
- 35 Search Insert Position
- 153 Find Minimum in Rotated Sorted Array

## Python Implementation
```python
def binary_search(arr, target):
    lo, hi = 0, len(arr) - 1
    while lo <= hi:
        mid = lo + (hi - lo) // 2
        if arr[mid] == target:
            return mid
        if arr[mid] < target:
            lo = mid + 1
        else:
            hi = mid - 1
    return -1


def lower_bound(arr, target):
    lo, hi = 0, len(arr)
    while lo < hi:
        mid = lo + (hi - lo) // 2
        if arr[mid] < target:
            lo = mid + 1
        else:
            hi = mid
    return lo
```
