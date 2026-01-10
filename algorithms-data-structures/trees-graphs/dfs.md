# Depth-First Search (DFS)

## Glossary
- DFS: graph traversal exploring as far as possible before backtracking. https://en.wikipedia.org/wiki/Depth-first_search
- Back edge: edge pointing to an ancestor in DFS tree (cycle detection). https://en.wikipedia.org/wiki/Depth-first_search#Applications
- Topological sort: ordering of DAG nodes via DFS postorder. https://en.wikipedia.org/wiki/Topological_sorting

## Usage (Specific)
- Cycle detection in dependency graphs (build systems, package managers).
- Find connected components or strongly connected components (with DFS-based algorithms).
- Pre/post-order tree traversals for serialization or validation.

## Average Time Complexity
- Average: O(V + E) for adjacency lists; space O(V) for visited/stack.

## Real-World Example
- NetworkX DFS traversal implementation. https://github.com/networkx/networkx/blob/main/networkx/algorithms/traversal/depth_first_search.py

## Tradeoffs and Failure Modes
- Recursive DFS can overflow stack on deep graphs; use iterative for large inputs.
- Graphs with high branching can cause large memory usage for recursion/stack.

## LeetCode
- 200 Number of Islands
- 207 Course Schedule
- 98 Validate Binary Search Tree

## Python Implementation
```python
def dfs(graph, start):
    visited = set()
    stack = [start]
    while stack:
        node = stack.pop()
        if node in visited:
            continue
        visited.add(node)
        for neighbor in graph.get(node, []):
            if neighbor not in visited:
                stack.append(neighbor)
    return visited
```
