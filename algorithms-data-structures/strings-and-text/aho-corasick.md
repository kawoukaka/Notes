# Aho-Corasick

## Glossary
- Trie: prefix tree for patterns. https://en.wikipedia.org/wiki/Trie
- Failure links: fallback edges for partial matches. https://en.wikipedia.org/wiki/Aho%E2%80%93Corasick_algorithm
- Output links: report matches for suffix patterns. https://en.wikipedia.org/wiki/Aho%E2%80%93Corasick_algorithm

## Usage (Specific)
- Multi-pattern scanning in security systems (WAF, IDS).
- Profanity or keyword filters for messaging systems.
- Log scanning for multiple error signatures.

## Average Time Complexity
- Average: O(n + m + z), where n is text length, m is total pattern length, z is matches.

## Real-World Example
- Hyperscan uses Aho-Corasick-style automata. https://github.com/intel/hyperscan

## Tradeoffs and Failure Modes
- Memory usage grows with pattern set size.
- Building automaton can be expensive; cache and reuse.

## LeetCode
- 211 Design Add and Search Words Data Structure (trie-based)
- 472 Concatenated Words

## Python Implementation
```python
from collections import deque

class Node:
    def __init__(self):
        self.children = {}
        self.fail = None
        self.output = []


def build_automaton(patterns):
    root = Node()
    for pat in patterns:
        node = root
        for ch in pat:
            node = node.children.setdefault(ch, Node())
        node.output.append(pat)

    q = deque()
    for child in root.children.values():
        child.fail = root
        q.append(child)

    while q:
        cur = q.popleft()
        for ch, nxt in cur.children.items():
            q.append(nxt)
            f = cur.fail
            while f and ch not in f.children:
                f = f.fail
            nxt.fail = f.children[ch] if f and ch in f.children else root
            nxt.output += nxt.fail.output
    return root


def aho_search(text, root):
    node = root
    matches = []
    for i, ch in enumerate(text):
        while node and ch not in node.children:
            node = node.fail
        node = node.children[ch] if node and ch in node.children else root
        for pat in node.output:
            matches.append((i - len(pat) + 1, pat))
    return matches
```
