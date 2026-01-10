# Reservoir Sampling

## Glossary
- Reservoir sampling: uniform sample from a stream of unknown size. https://en.wikipedia.org/wiki/Reservoir_sampling
- Single-pass algorithm: processes items once. https://en.wikipedia.org/wiki/Reservoir_sampling
- Sample size k: fixed size of reservoir. https://en.wikipedia.org/wiki/Reservoir_sampling

## Usage (Specific)
- Telemetry sampling for large log streams.
- Online sampling for A/B test data collection.
- Debugging by capturing representative events.

## Average Time Complexity
- Average: O(1) per element; space O(k).

## Real-World Example
- Apache Beam uses reservoir sampling for sampling transforms. https://github.com/apache/beam

## Tradeoffs and Failure Modes
- Requires good RNG; bias leads to skewed samples.
- Does not support weighted sampling without modification.

## LeetCode
- 382 Linked List Random Node
- 398 Random Pick Index

## Python Implementation
```python
import random

def reservoir_sample(stream, k):
    reservoir = []
    for i, item in enumerate(stream):
        if i < k:
            reservoir.append(item)
        else:
            j = random.randint(0, i)
            if j < k:
                reservoir[j] = item
    return reservoir
```
