# Greedy Algorithms

## Glossary
- Exchange argument: proof technique for greedy optimality. https://en.wikipedia.org/wiki/Greedy_algorithm
- Matroid: structure where greedy yields optimum. https://en.wikipedia.org/wiki/Matroid
- Feasibility invariant: condition preserved by greedy choice. https://en.wikipedia.org/wiki/Greedy_algorithm

## Usage (Specific)
- Bandwidth allocation when tasks have strict deadlines (earliest deadline first).
- Cache eviction decisions when recency/frequency approximations suffice.
- Interval selection and job scheduling with deadlines.

## Average Time Complexity
- Average: O(n log n) when sorting is required; O(n) otherwise.

## Real-World Example
- Kubernetes scheduler uses greedy heuristics for bin-packing. https://github.com/kubernetes/kubernetes

## Tradeoffs and Failure Modes
- Greedy can be suboptimal without a proof or matroid structure.
- Local optima may block better global configurations.
- Needs careful tie-breaking to avoid edge-case failures.

## LeetCode
- 435 Non-overlapping Intervals
- 621 Task Scheduler
- 134 Gas Station

## Python Implementation
```python
def interval_scheduling(intervals):
    intervals.sort(key=lambda x: x[1])
    result = []
    end = float("-inf")
    for start, finish in intervals:
        if start >= end:
            result.append((start, finish))
            end = finish
    return result
```
