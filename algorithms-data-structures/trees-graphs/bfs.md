# Breadth-First Search (BFS)

## Glossary
- BFS: graph traversal exploring neighbors level by level. https://en.wikipedia.org/wiki/Breadth-first_search
- Queue: FIFO structure used to track frontier. https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
- Level order: traversal by distance from source. https://en.wikipedia.org/wiki/Breadth-first_search

## Usage (Specific)
- Shortest path in unweighted graphs (network hops, routing with equal cost).
- Minimum steps problems (word ladder, grid shortest path).
- Level order traversal in trees for analytics or layout.

## Average Time Complexity
- Average: O(V + E) for adjacency lists; space O(V).

## Real-World Example
- NetworkX BFS traversal implementation. https://github.com/networkx/networkx/blob/main/networkx/algorithms/traversal/breadth_first_search.py

## Tradeoffs and Failure Modes
- Memory usage grows with frontier size.
- Requires a queue; avoid recursion to prevent stack overflow.

## LeetCode
- 102 Binary Tree Level Order Traversal
- 127 Word Ladder
- 1091 Shortest Path in Binary Matrix

## Python Implementation
```python
from collections import deque


def bfs(graph, start):
    visited = set([start])
    q = deque([start])
    while q:
        node = q.popleft()
        for neighbor in graph.get(node, []):
            if neighbor not in visited:
                visited.add(neighbor)
                q.append(neighbor)
    return visited
```
