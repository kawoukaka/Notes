# Suffix Array

## Glossary
- Suffix array: sorted array of all suffixes. https://en.wikipedia.org/wiki/Suffix_array
- LCP array: longest common prefix between adjacent suffixes. https://en.wikipedia.org/wiki/LCP_array
- SA-IS: linear-time suffix array construction. https://en.wikipedia.org/wiki/SA-IS

## Usage (Specific)
- Fast substring queries and pattern matching in large text corpora.
- Build search index for static documents or logs.
- Longest repeated substring or pattern frequency analysis.

## Average Time Complexity
- Average: O(n log n) for common constructions; space O(n).

## Real-World Example
- Suffix array implementation in SDSL (succinct data structures). https://github.com/simongog/sdsl-lite

## Tradeoffs and Failure Modes
- Construction is non-trivial; heavy constants for large alphabets.
- Requires extra memory for LCP and rank arrays.

## LeetCode
- 1044 Longest Duplicate Substring
- 1062 Longest Repeating Substring

## Python Implementation
```python
def build_suffix_array(s):
    return sorted(range(len(s)), key=lambda i: s[i:])


def lcp_array(s, sa):
    n = len(s)
    rank = [0] * n
    for i, idx in enumerate(sa):
        rank[idx] = i
    lcp = [0] * (n - 1)
    h = 0
    for i in range(n):
        if rank[i] == n - 1:
            h = 0
            continue
        j = sa[rank[i] + 1]
        while i + h < n and j + h < n and s[i + h] == s[j + h]:
            h += 1
        lcp[rank[i]] = h
        if h > 0:
            h -= 1
    return lcp
```
