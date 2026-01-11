# Backtracking

## Glossary
- Backtracking: depth-first search with undo/redo choices. https://en.wikipedia.org/wiki/Backtracking
- Pruning: early exit to cut impossible branches. https://en.wikipedia.org/wiki/Branch_and_bound
- Constraint satisfaction: search over assignments under constraints. https://en.wikipedia.org/wiki/Constraint_satisfaction_problem

## Usage (Specific)
- Generate valid configurations (scheduling, seating, puzzle solvers).
- Search for feasible deployment plans under hard constraints.
- Solve combinatorial enumeration with pruning (feature flag combinations).

## Average Time Complexity
- Average: depends on pruning; worst-case O(b^d) with branching factor b and depth d.

## Real-World Example
- Git uses a form of backtracking when it searches commit history for merges or conflict resolution. https://git-scm.com/docs/git-rev-list

## Tradeoffs and Failure Modes
- Exponential blow-up without pruning.
- Requires good heuristics (ordering, constraint propagation) for scale.

## LeetCode
- 46 Permutations
- 39 Combination Sum
- 79 Word Search

## Python Implementation
```python
def permutations(nums):
    result = []
    used = [False] * len(nums)

    def dfs(path):
        if len(path) == len(nums):
            result.append(path[:])
            return
        for i, val in enumerate(nums):
            if used[i]:
                continue
            used[i] = True
            path.append(val)
            dfs(path)
            path.pop()
            used[i] = False

    dfs([])
    return result
```

```python
def combinations(nums, k):
    result = []

    def dfs(start, path):
        if len(path) == k:
            result.append(path[:])
            return
        for i in range(start, len(nums)):
            path.append(nums[i])
            dfs(i + 1, path)
            path.pop()

    dfs(0, [])
    return result
```
