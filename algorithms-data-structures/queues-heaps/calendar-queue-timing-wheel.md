# Calendar Queue / Timing Wheel

## Glossary
- Timing wheel: bucketed timer scheduler. https://en.wikipedia.org/wiki/Timing_wheel
- Calendar queue: priority queue optimized for time-ordered events. https://en.wikipedia.org/wiki/Calendar_queue
- Timer wheel hierarchy: multi-level wheels for wide time ranges. https://en.wikipedia.org/wiki/Timing_wheel

## Usage (Specific)
- Retry scheduling for distributed job systems.
- TTL expiration for cache entries or sessions.
- Delayed message delivery in queues.

## Average Time Complexity
- Average: O(1) amortized per timer for timing wheels; calendar queues depend on bucket tuning.

## Real-World Example
- Netty's hashed wheel timer. https://github.com/netty/netty

## Tradeoffs and Failure Modes
- Requires tuning tick size and wheel size.
- Poor tuning causes uneven bucket loads and latency spikes.

## LeetCode
- 622 Design Circular Queue (timing wheel uses ring buffer concepts)

## Python Implementation
```python
import time

class TimingWheel:
    def __init__(self, tick_seconds, slots):
        self.tick = tick_seconds
        self.slots = [[] for _ in range(slots)]
        self.current = 0

    def add(self, delay_seconds, callback):
        ticks = int(delay_seconds / self.tick)
        slot = (self.current + ticks) % len(self.slots)
        self.slots[slot].append(callback)

    def advance(self):
        callbacks = self.slots[self.current]
        self.slots[self.current] = []
        self.current = (self.current + 1) % len(self.slots)
        for cb in callbacks:
            cb()
```
