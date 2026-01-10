# Queue / Deque

## Glossary
- Queue: FIFO structure for ordered processing. https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
- Deque: double-ended queue. https://en.wikipedia.org/wiki/Double-ended_queue
- Backpressure: control producer rate when consumers lag. https://en.wikipedia.org/wiki/Backpressure_(computer_science)

## Usage (Specific)
- Request buffering between load balancer and workers.
- Async job pipelines with bounded concurrency.
- Streaming ingestion where ordering is required.

## Average Time Complexity
- Average: enqueue/dequeue O(1); space O(n).

## Real-World Example
- Python `collections.deque` implementation. https://github.com/python/cpython/blob/main/Modules/_collectionsmodule.c

## Tradeoffs and Failure Modes
- Unbounded queues can cause memory blowups; enforce max size.
- Head-of-line blocking if tasks vary widely in duration.

## LeetCode
- 232 Implement Queue using Stacks
- 933 Number of Recent Calls

## Python Implementation
```python
from collections import deque

class Queue:
    def __init__(self):
        self.q = deque()

    def enqueue(self, value):
        self.q.append(value)

    def dequeue(self):
        if not self.q:
            return None
        return self.q.popleft()
```
