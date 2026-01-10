# Radix Sort

## Glossary
- LSD radix: process least significant digit first. https://en.wikipedia.org/wiki/Radix_sort
- MSD radix: process most significant digit first. https://en.wikipedia.org/wiki/Radix_sort
- Counting sort: stable counting by digit. https://en.wikipedia.org/wiki/Counting_sort

## Usage (Specific)
- Sort fixed-width numeric IDs (order IDs, timestamps, hashes) where comparisons are expensive.
- Batch sort large volumes of integers in ETL pipelines where key ranges are known.
- Multi-key sort by processing digits for each key in sequence (stable by digit).

## Average Time Complexity
- Average: O(k * n) where k is digit count; space O(n + k).

## Real-World Example
- Reference implementation in TheAlgorithms (Python). https://github.com/TheAlgorithms/Python/blob/master/sorts/radix_sort.py

## Tradeoffs and Failure Modes
- Requires extra memory for counting buckets.
- Not comparison-based; only works when digits can be extracted efficiently.
- MSD radix is sensitive to skewed prefixes and can degrade without careful partitioning.

## LeetCode
- 164 Maximum Gap (radix sort is a common solution)
- 347 Top K Frequent Elements (radix-like bucket approach)

## Python Implementation
```python
def radix_sort(arr):
    if not arr:
        return arr
    max_num = max(arr)
    exp = 1
    while max_num // exp > 0:
        counting_sort_by_digit(arr, exp)
        exp *= 10
    return arr


def counting_sort_by_digit(arr, exp):
    n = len(arr)
    output = [0] * n
    count = [0] * 10

    for num in arr:
        index = (num // exp) % 10
        count[index] += 1

    for i in range(1, 10):
        count[i] += count[i - 1]

    for i in range(n - 1, -1, -1):
        index = (arr[i] // exp) % 10
        output[count[index] - 1] = arr[i]
        count[index] -= 1

    for i in range(n):
        arr[i] = output[i]
```
