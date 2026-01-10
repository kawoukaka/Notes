# Suffix Tree

## Glossary
- Suffix tree: compressed trie of all suffixes. https://en.wikipedia.org/wiki/Suffix_tree
- Ukkonen's algorithm: online linear-time construction. https://en.wikipedia.org/wiki/Ukkonen%27s_algorithm
- Implicit suffix tree: construction stage without explicit leaf ends. https://en.wikipedia.org/wiki/Ukkonen%27s_algorithm

## Usage (Specific)
- Multiple substring queries on a static corpus with many patterns.
- Find longest common substring across two strings.
- Detect repeated motifs in bioinformatics sequences.

## Average Time Complexity
- Average: O(n) build with Ukkonen; queries O(m) for pattern length m.

## Real-World Example
- Suffix tree reference in Ukkonen implementation (Python). https://github.com/ptrus/suffix-trees

## Tradeoffs and Failure Modes
- High memory overhead; can be 10x input size.
- Complex to implement correctly; suffix array often preferred.

## LeetCode
- 1044 Longest Duplicate Substring (suffix tree approach)
- 1062 Longest Repeating Substring

## Python Implementation
```python
class SuffixTrieNode:
    def __init__(self):
        self.children = {}


def build_suffix_trie(s):
    root = SuffixTrieNode()
    for i in range(len(s)):
        node = root
        for ch in s[i:]:
            node = node.children.setdefault(ch, SuffixTrieNode())
    return root
```
