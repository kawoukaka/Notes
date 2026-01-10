# Heavy Hitters (Misra-Gries)

## Glossary
- Heavy hitters: items with frequency above a threshold. https://en.wikipedia.org/wiki/Heavy_hitters
- Misra-Gries: streaming algorithm for frequent items. https://en.wikipedia.org/wiki/Misra%E2%80%93Gries
- Error bound: max overcount based on k. https://en.wikipedia.org/wiki/Misra%E2%80%93Gries

## Usage (Specific)
- Identify top endpoints in API traffic.
- Detect trending queries or hashtags.
- Allocate cache space to most frequent keys.

## Average Time Complexity
- Average: O(1) per update with k counters; space O(k).

## Real-World Example
- Apache DataSketches frequent items. https://github.com/apache/datasketches

## Tradeoffs and Failure Modes
- Only guarantees accuracy for items above threshold.
- Requires choosing k based on acceptable error.

## LeetCode
- 347 Top K Frequent Elements
- 692 Top K Frequent Words

## Python Implementation
```python
def misra_gries(stream, k):
    counters = {}
    for item in stream:
        if item in counters:
            counters[item] += 1
        elif len(counters) < k - 1:
            counters[item] = 1
        else:
            to_delete = []
            for key in counters:
                counters[key] -= 1
                if counters[key] == 0:
                    to_delete.append(key)
            for key in to_delete:
                del counters[key]
    return counters
```
