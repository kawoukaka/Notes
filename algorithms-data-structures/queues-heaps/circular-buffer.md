# Circular Buffer (Ring Buffer)

## Glossary
- Circular buffer: fixed-size buffer with wrap-around indices. https://en.wikipedia.org/wiki/Circular_buffer
- Producer-consumer: concurrent producers and consumers. https://en.wikipedia.org/wiki/Producer%E2%80%93consumer_problem
- False sharing: cache contention across threads. https://en.wikipedia.org/wiki/False_sharing

## Usage (Specific)
- Log buffering before batch flush to disk.
- Telemetry ingestion with bounded memory.
- Audio/video streaming with fixed latency window.

## Average Time Complexity
- Average: read/write O(1); space O(n).

## Real-World Example
- LMAX Disruptor ring buffer. https://github.com/LMAX-Exchange/disruptor

## Tradeoffs and Failure Modes
- Overwrite behavior must be defined (drop oldest vs block).
- Off-by-one errors in wrap-around are common.
- Multi-producer cases require careful synchronization.

## LeetCode
- 622 Design Circular Queue
- 641 Design Circular Deque

## Python Implementation
```python
class RingBuffer:
    def __init__(self, size):
        self.size = size
        self.data = [None] * size
        self.head = 0
        self.tail = 0
        self.full = False

    def write(self, value):
        self.data[self.tail] = value
        if self.full:
            self.head = (self.head + 1) % self.size
        self.tail = (self.tail + 1) % self.size
        self.full = self.tail == self.head

    def read(self):
        if self.is_empty():
            return None
        value = self.data[self.head]
        self.head = (self.head + 1) % self.size
        self.full = False
        return value

    def is_empty(self):
        return (not self.full) and (self.head == self.tail)
```
