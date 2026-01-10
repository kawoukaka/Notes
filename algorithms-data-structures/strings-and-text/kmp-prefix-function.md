# Prefix Function / KMP

## Glossary
- Prefix function (pi): length of longest proper prefix that is also suffix. https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm
- Border: string that is both prefix and suffix. https://en.wikipedia.org/wiki/Border_(string)
- Failure function: table of fallback positions. https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm

## Usage (Specific)
- Scan large logs for fixed signatures without backtracking.
- Stream processing where reprocessing is costly (network IDS patterns).
- Detect repeated patterns or period in strings using prefix function.

## Average Time Complexity
- Average: O(n + m) for pattern length m and text length n; space O(m).

## Real-World Example
- Rust `memchr` uses KMP-like ideas for some searches. https://github.com/BurntSushi/memchr

## Tradeoffs and Failure Modes
- Requires preprocessing; overhead is not worth it for very short patterns.
- Implementation errors often come from prefix table indexing.

## LeetCode
- 28 Find the Index of the First Occurrence in a String
- 459 Repeated Substring Pattern

## Python Implementation
```python
def kmp_search(text, pattern):
    if not pattern:
        return 0
    lps = build_lps(pattern)
    i = j = 0
    while i < len(text):
        if text[i] == pattern[j]:
            i += 1
            j += 1
            if j == len(pattern):
                return i - j
        else:
            if j != 0:
                j = lps[j - 1]
            else:
                i += 1
    return -1


def build_lps(pattern):
    lps = [0] * len(pattern)
    length = 0
    i = 1
    while i < len(pattern):
        if pattern[i] == pattern[length]:
            length += 1
            lps[i] = length
            i += 1
        else:
            if length != 0:
                length = lps[length - 1]
            else:
                lps[i] = 0
                i += 1
    return lps
```
