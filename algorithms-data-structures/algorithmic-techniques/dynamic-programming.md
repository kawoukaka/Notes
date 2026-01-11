# Dynamic Programming (Technique)

## What It Is
- Break a problem into overlapping subproblems and store results to avoid recomputation.

## When to Use
- Optimal substructure: solution depends on optimal solutions to subproblems.
- Overlapping subproblems: repeated states appear in recursion.

## Real-World Usage
- Pricing and capacity planning with discrete constraints.
- Recommendation re-ranking with budget or diversity constraints.
- Text diff and sequence alignment in developer tools.

## LeetCode
- 198 House Robber
- 322 Coin Change
- 1143 Longest Common Subsequence
- 72 Edit Distance

## Senior Mindset
- Start by defining the state and transition.
- Use memoization for sparse states; tabulation for dense states.
- Watch memory growth; compress dimensions when possible.

# Memoization vs Tabulation

## What Is Different
- Memoization: top-down recursion with a cache; compute subproblems on demand.
- Tabulation: bottom-up iteration; compute all subproblems in a table.
- Memoization is easier to write for complex transitions; tabulation is often faster and avoids recursion limits.

## When to Prefer Each
- Memoization: sparse state space, irregular transitions, or complex recursion.
- Tabulation: dense state space, clear ordering, and performance-critical paths.

## How to Derive Them From the Problem
1. Define the state: what variables uniquely describe a subproblem.
2. Define transitions: how to move from state to smaller states.
3. Identify base cases.
4. Decide evaluation order:
   - If dependencies form a simple order, use tabulation.
   - If dependencies are irregular or sparse, use memoization.

## Example Mindset
- Ask: can I express the answer for state (i, j) in terms of smaller states?
- If yes, write the recurrence and then choose top-down (memoization) or bottom-up (tabulation).
- Validate with small examples and ensure no missing base cases.
