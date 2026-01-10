# Dynamic Programming (DP)

## Glossary
- Optimal substructure: global optimum from optimal subproblems. https://en.wikipedia.org/wiki/Optimal_substructure
- Overlapping subproblems: repeated subproblems cached via memoization. https://en.wikipedia.org/wiki/Dynamic_programming
- State compression: reduce DP state dimensionality. https://cp-algorithms.com/dynamic_programming/profile-dynamics.html

## Usage (Specific)
- Resource allocation with per-step constraints (capacity planning by time slice).
- Pricing optimization with discrete tiers (compute best revenue per bucket).
- Sequence alignment or diff computations for large text pipelines.

## Average Time Complexity
- Average: O(S * T) where S is state count and T transitions per state.

## Real-World Example
- Google's OR-Tools uses DP for certain optimization models. https://github.com/google/or-tools

## Tradeoffs and Failure Modes
- State explosion can blow memory; use pruning or compress dimensions.
- Memoization needs bounded key growth or LRU eviction for large inputs.
- Iterative DP avoids recursion depth limits.

## LeetCode
- 198 House Robber
- 322 Coin Change
- 1143 Longest Common Subsequence

## Python Implementation
```python
from functools import lru_cache

def coin_change(coins, amount):
    @lru_cache(None)
    def dp(remaining):
        if remaining == 0:
            return 0
        if remaining < 0:
            return float("inf")
        best = min(dp(remaining - c) + 1 for c in coins)
        return best

    result = dp(amount)
    return -1 if result == float("inf") else result
```
