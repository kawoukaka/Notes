# Merge Sort

## Glossary
- Stability: equal keys keep their original order. https://en.wikipedia.org/wiki/Sorting_algorithm#Stability
- External sorting: sort data larger than memory using disk-based runs. https://en.wikipedia.org/wiki/External_sorting
- K-way merge: merge multiple sorted runs efficiently. https://en.wikipedia.org/wiki/K-way_merge_algorithm

## Usage (Specific)
- Stable sorting of records where secondary ordering matters (e.g., sort by status then timestamp).
- External sort for large log files or ETL pipelines (create sorted runs, then merge).
- Merge multiple pre-sorted streams (e.g., time-ordered event feeds).

## Average Time Complexity
- Average: O(n log n); space O(n).

## Real-World Example
- CPython list sort (Timsort) relies heavily on merging runs. https://github.com/python/cpython/blob/main/Objects/listobject.c

## Tradeoffs and Failure Modes
- Requires O(n) extra memory for arrays (top-down merge).
- Stable and predictable O(n log n), but higher constant factors than quicksort.
- External sort needs careful tuning of run size and I/O batching.

## LeetCode
- 148 Sort List
- 315 Count of Smaller Numbers After Self
- 493 Reverse Pairs

## Python Implementation
```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    return merge(left, right)


def merge(left, right):
    merged = []
    i = j = 0
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            merged.append(left[i])
            i += 1
        else:
            merged.append(right[j])
            j += 1
    merged.extend(left[i:])
    merged.extend(right[j:])
    return merged
```
