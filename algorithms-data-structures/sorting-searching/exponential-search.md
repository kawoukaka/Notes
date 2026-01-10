# Exponential Search (Galloping)

## Glossary
- Exponential search: find a range by doubling then binary search. https://en.wikipedia.org/wiki/Exponential_search
- Galloping mode: accelerated merge scanning in Timsort. https://en.wikipedia.org/wiki/Timsort
- Unbounded search: searching when length is unknown. https://en.wikipedia.org/wiki/Exponential_search

## Usage (Specific)
- Search in paged or remote data where length is unknown (APIs, log stores).
- Accelerate merges of uneven runs during external sort.
- Reduce round-trips by quickly finding a tight search window.

## Average Time Complexity
- Average: O(log i) where i is target index; space O(1).

## Real-World Example
- CPython Timsort implements galloping for merges. https://github.com/python/cpython/blob/main/Objects/listobject.c

## Tradeoffs and Failure Modes
- Doubles can overshoot; ensure bounds checks for out-of-range reads.
- Best when target is near the beginning or length is unknown.
- Requires a sorted array or monotonic predicate.

## LeetCode
- 702 Search in a Sorted Array of Unknown Size

## Python Implementation
```python
def exponential_search(arr, target):
    if not arr:
        return -1
    if arr[0] == target:
        return 0

    i = 1
    n = len(arr)
    while i < n and arr[i] < target:
        i *= 2

    return binary_search(arr, target, i // 2, min(i, n - 1))


def binary_search(arr, target, lo, hi):
    while lo <= hi:
        mid = lo + (hi - lo) // 2
        if arr[mid] == target:
            return mid
        if arr[mid] < target:
            lo = mid + 1
        else:
            hi = mid - 1
    return -1
```
