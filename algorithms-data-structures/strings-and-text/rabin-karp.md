# Rabin-Karp

## Glossary
- Rolling hash: hash updated in O(1) per shift. https://en.wikipedia.org/wiki/Rolling_hash
- Modulus: reduces hash to bounded integer range. https://en.wikipedia.org/wiki/Modular_arithmetic
- Spurious hit: hash match without actual match. https://en.wikipedia.org/wiki/Rabin%E2%80%93Karp_algorithm

## Usage (Specific)
- Multi-pattern search by hashing many patterns of same length.
- Plagiarism detection for large documents (n-gram hashing).
- Streaming substring search with limited memory.

## Average Time Complexity
- Average: O(n + m) with low collision rate; worst-case O(nm).

## Real-World Example
- Reference implementation in TheAlgorithms (Python). https://github.com/TheAlgorithms/Python/blob/master/strings/rabin_karp.py

## Tradeoffs and Failure Modes
- Collisions require verifying matches; use double hashing to reduce risk.
- Sensitive to modulus choice; small mod increases collisions.

## LeetCode
- 28 Find the Index of the First Occurrence in a String (hash-based solutions)
- 1044 Longest Duplicate Substring

## Python Implementation
```python
def rabin_karp(text, pattern, base=256, mod=10**9 + 7):
    n, m = len(text), len(pattern)
    if m == 0 or m > n:
        return -1
    h = pow(base, m - 1, mod)
    p_hash = t_hash = 0
    for i in range(m):
        p_hash = (p_hash * base + ord(pattern[i])) % mod
        t_hash = (t_hash * base + ord(text[i])) % mod
    for i in range(n - m + 1):
        if p_hash == t_hash and text[i:i + m] == pattern:
            return i
        if i < n - m:
            t_hash = (t_hash - ord(text[i]) * h) % mod
            t_hash = (t_hash * base + ord(text[i + m])) % mod
            t_hash %= mod
    return -1
```
