# Levenshtein / Edit Distance

## Glossary
- Edit distance: minimum edits between two strings. https://en.wikipedia.org/wiki/Levenshtein_distance
- Dynamic programming table: matrix of partial distances. https://en.wikipedia.org/wiki/Levenshtein_distance
- Wagner-Fischer algorithm: classic DP method. https://en.wikipedia.org/wiki/Levenshtein_distance

## Usage (Specific)
- Fuzzy search for user inputs (typo-tolerant search).
- Duplicate detection and data cleanup in customer records.
- Ranking search suggestions by similarity.

## Average Time Complexity
- Average: O(n * m) time, O(n * m) space; can be optimized to O(min(n, m)) space.

## Real-World Example
- SymSpell uses edit distance concepts for suggestions. https://github.com/wolfgarbe/SymSpell

## Tradeoffs and Failure Modes
- Quadratic cost is high for long strings; use bounded distance or n-gram filters.
- Unicode normalization affects distance results; normalize first.

## LeetCode
- 72 Edit Distance
- 583 Delete Operation for Two Strings

## Python Implementation
```python
def edit_distance(a, b):
    if len(a) < len(b):
        a, b = b, a
    prev = list(range(len(b) + 1))
    for i, ca in enumerate(a, 1):
        curr = [i]
        for j, cb in enumerate(b, 1):
            if ca == cb:
                curr.append(prev[j - 1])
            else:
                curr.append(1 + min(prev[j], curr[j - 1], prev[j - 1]))
        prev = curr
    return prev[-1]
```
