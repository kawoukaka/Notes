# Priority Queue / Heap

## Glossary
- Priority queue: pops highest/lowest priority element. https://en.wikipedia.org/wiki/Priority_queue
- Binary heap: array-backed heap structure. https://en.wikipedia.org/wiki/Binary_heap
- Decrease-key: update priority for an element. https://en.wikipedia.org/wiki/Heap_(data_structure)

## Usage (Specific)
- Scheduling tasks by deadline or priority (job runners).
- Top-k retrieval in ranking systems.
- Event simulation where next event time matters.

## Average Time Complexity
- Average: push/pop O(log n), peek O(1).

## Real-World Example
- CPython `heapq` module. https://github.com/python/cpython/blob/main/Lib/heapq.py

## Tradeoffs and Failure Modes
- Updates require decrease-key; often emulated by pushing new entries.
- Heap can grow with stale entries; use lazy deletion or index map.

## LeetCode
- 215 Kth Largest Element in an Array
- 347 Top K Frequent Elements
- 703 Kth Largest Element in a Stream

## Python Implementation
```python
import heapq

class PriorityQueue:
    def __init__(self):
        self.heap = []

    def push(self, priority, value):
        heapq.heappush(self.heap, (priority, value))

    def pop(self):
        if not self.heap:
            return None
        return heapq.heappop(self.heap)
```
