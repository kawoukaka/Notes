# Interpolation Search

## Glossary
- Interpolation formula: estimate position based on key distribution. https://en.wikipedia.org/wiki/Interpolation_search
- Uniform distribution: keys spread evenly across range. https://en.wikipedia.org/wiki/Uniform_distribution
- Search invariant: condition preserved each iteration. https://en.wikipedia.org/wiki/Loop_invariant

## Usage (Specific)
- Search in large, uniformly distributed numeric keys (e.g., time-based indices with fixed step).
- Useful when comparisons are cheap and distribution is predictable.
- Not ideal for skewed or clustered data (performance degrades toward O(n)).

## Average Time Complexity
- Average: O(log log n) on uniform keys; space O(1).

## Real-World Example
- Reference implementation in TheAlgorithms (Python). https://github.com/TheAlgorithms/Python/blob/master/searches/interpolation_search.py

## Tradeoffs and Failure Modes
- Requires numeric keys and an assumption about distribution.
- Sensitive to outliers; worst-case O(n).
- Needs careful bounds handling to avoid division by zero.

## LeetCode
- N/A (often discussed as an optimization over binary search, not a standalone problem)

## Python Implementation
```python
def interpolation_search(arr, target):
    lo, hi = 0, len(arr) - 1
    while lo <= hi and arr[lo] <= target <= arr[hi]:
        if arr[hi] == arr[lo]:
            if arr[lo] == target:
                return lo
            return -1
        pos = lo + int((hi - lo) * (target - arr[lo]) / (arr[hi] - arr[lo]))
        if arr[pos] == target:
            return pos
        if arr[pos] < target:
            lo = pos + 1
        else:
            hi = pos - 1
    return -1
```
