# Sliding Window

## Glossary
- Sliding window: maintain a moving subarray over a sequence. https://en.wikipedia.org/wiki/Sliding_window_protocol
- Two pointers: technique using left/right bounds. https://en.wikipedia.org/wiki/Two-pointer_technique
- Window invariant: condition preserved while expanding/contracting. https://cp-algorithms.com/others/two-pointer-technique.html

## Usage (Specific)
- Real-time rate limiting based on rolling windows.
- Subarray aggregation (max sum, min length) in streaming analytics.
- Deduplicate or count distinct elements in fixed-size windows.

## Average Time Complexity
- Average: O(n) for linear passes with monotonic adjustments; space O(1) or O(k).

## Real-World Example
- Apache Flink window operators for stream processing. https://github.com/apache/flink

## Tradeoffs and Failure Modes
- Off-by-one errors in window bounds are common.
- Maintaining invariants with multiset or heap can raise complexity to O(n log k).

## LeetCode
- 3 Longest Substring Without Repeating Characters
- 76 Minimum Window Substring
- 239 Sliding Window Maximum

## Python Implementation
```python
def min_subarray_len(target, nums):
    left = 0
    total = 0
    best = float("inf")
    for right, value in enumerate(nums):
        total += value
        while total >= target:
            best = min(best, right - left + 1)
            total -= nums[left]
            left += 1
    return 0 if best == float("inf") else best
```
