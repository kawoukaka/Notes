# Interval Scheduling

## Glossary
- Interval scheduling: select max non-overlapping intervals. https://en.wikipedia.org/wiki/Interval_scheduling
- Earliest finish time: greedy rule for optimality. https://en.wikipedia.org/wiki/Interval_scheduling
- Weighted interval scheduling: maximize weight, requires DP. https://en.wikipedia.org/wiki/Interval_scheduling#Weighted_interval_scheduling

## Usage (Specific)
- Batch job placement on shared resources with non-overlap constraints.
- Calendar conflict resolution for booking systems.
- Scheduling maintenance windows with minimal service disruption.

## Average Time Complexity
- Average: O(n log n) for sorting + O(n) scan.

## Real-World Example
- Apache Airflow scheduling logic for non-overlapping task windows. https://github.com/apache/airflow

## Tradeoffs and Failure Modes
- Greedy works for unweighted; weighted requires DP or segment tree.
- Time normalization is required for large timestamp ranges.
- Edge case handling when intervals touch (inclusive/exclusive) matters.

## LeetCode
- 435 Non-overlapping Intervals
- 1235 Maximum Profit in Job Scheduling

## Python Implementation
```python
def max_non_overlapping(intervals):
    intervals.sort(key=lambda x: x[1])
    count = 0
    end = float("-inf")
    for start, finish in intervals:
        if start >= end:
            count += 1
            end = finish
    return count
```
