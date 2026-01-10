# Quick Sort

## Glossary
- Introsort: hybrid quicksort that falls back to heap sort to avoid worst-case O(n^2). https://en.wikipedia.org/wiki/Introsort
- Random pivot: pivot chosen uniformly at random to reduce adversarial inputs. https://en.wikipedia.org/wiki/Quicksort#Choice_of_pivot
- Hoare partition scheme: partitioning approach that swaps from both ends. https://en.wikipedia.org/wiki/Quicksort#Hoare_partition_scheme

## Usage (Specific)
- Sort large in-memory arrays of primitive types where stability is not required.
- Sort per-shard chunks before a k-way merge in an external sort pipeline.
- Sort hot-path data with predictable average-case latency (e.g., ranking results for a single request).

## Average Time Complexity
- Average: O(n log n) comparisons; space O(log n) for recursion.

## Real-World Example
- OpenJDK uses dual-pivot quicksort for primitive arrays in `Arrays.sort`. https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/util/DualPivotQuicksort.java

## Tradeoffs and Failure Modes
- Worst-case O(n^2) if pivot choices are poor or inputs are adversarial.
- Not stable; equal keys can reorder.
- Recursion depth can overflow for large arrays without safeguards.

## LeetCode
- 912 Sort an Array
- 215 Kth Largest Element in an Array (via partition)
- 973 K Closest Points to Origin (partition-based selection)

## Python Implementation
```python
import random

def quick_sort(arr):
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

    def sort(lo, hi):
        if lo >= hi:
            return
        p = partition(lo, hi)
        sort(lo, p - 1)
        sort(p + 1, hi)

    sort(0, len(arr) - 1)
    return arr
```
