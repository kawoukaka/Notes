# Max Flow / Min-Cost Flow

## Glossary
- Max flow: maximum feasible flow in a network. https://en.wikipedia.org/wiki/Maximum_flow_problem
- Min-cost flow: minimum cost for sending flow. https://en.wikipedia.org/wiki/Minimum-cost_flow_problem
- Residual graph: remaining capacity after flow. https://en.wikipedia.org/wiki/Residual_network

## Usage (Specific)
- Assign workers to jobs with capacity constraints (task routing).
- Bandwidth allocation across links with total capacity.
- Cost-aware routing for logistics and supply chain planning.

## Average Time Complexity
- Average (Edmonds-Karp): O(V * E^2).

## Real-World Example
- NetworkX flow algorithms. https://github.com/networkx/networkx

## Tradeoffs and Failure Modes
- Large graphs lead to high memory/time; use optimized implementations.
- Integer overflow possible if costs are large; use 64-bit.
- Need careful modeling to avoid negative cycles in min-cost flow.

## LeetCode
- 743 Network Delay Time (shortest path related)
- 787 Cheapest Flights Within K Stops (min-cost path variant)

## Python Implementation
```python
from collections import deque

def edmonds_karp(capacity, source, sink):
    n = len(capacity)
    flow = 0
    parent = [-1] * n

    def bfs():
        for i in range(n):
            parent[i] = -1
        parent[source] = source
        q = deque([source])
        while q:
            u = q.popleft()
            for v in range(n):
                if parent[v] == -1 and capacity[u][v] > 0:
                    parent[v] = u
                    if v == sink:
                        return True
                    q.append(v)
        return False

    while bfs():
        path_flow = float("inf")
        v = sink
        while v != source:
            u = parent[v]
            path_flow = min(path_flow, capacity[u][v])
            v = u
        v = sink
        while v != source:
            u = parent[v]
            capacity[u][v] -= path_flow
            capacity[v][u] += path_flow
            v = u
        flow += path_flow

    return flow
```
