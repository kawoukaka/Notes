# Knapsack Variants

## Glossary
- 0/1 knapsack: each item chosen at most once. https://en.wikipedia.org/wiki/Knapsack_problem
- Unbounded knapsack: items can be reused. https://en.wikipedia.org/wiki/Unbounded_knapsack_problem
- FPTAS: approximation scheme for large instances. https://en.wikipedia.org/wiki/Fully_polynomial-time_approximation_scheme

## Usage (Specific)
- Feature rollout under resource caps (feature flags with capacity constraints).
- Budget allocation across ads or campaigns with discrete options.
- VM placement with limited CPU/memory units.

## Average Time Complexity
- Average: O(n * W) for 0/1 DP with capacity W; space O(W).

## Real-World Example
- Google OR-Tools knapsack solver. https://github.com/google/or-tools

## Tradeoffs and Failure Modes
- DP is pseudo-polynomial in capacity; infeasible for large weights.
- Approximation needed for large-scale or real-time systems.
- Order of item processing matters for 1D DP in unbounded knapsack.

## LeetCode
- 416 Partition Equal Subset Sum
- 494 Target Sum
- 1049 Last Stone Weight II

## Python Implementation
```python
def knapsack_01(weights, values, capacity):
    n = len(weights)
    dp = [0] * (capacity + 1)
    for i in range(n):
        w, v = weights[i], values[i]
        for c in range(capacity, w - 1, -1):
            dp[c] = max(dp[c], dp[c - w] + v)
    return dp[capacity]
```
