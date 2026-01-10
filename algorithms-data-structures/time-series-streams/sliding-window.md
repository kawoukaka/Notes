# Sliding Window

## Glossary
- Sliding window: moving subarray over a sequence. https://en.wikipedia.org/wiki/Sliding_window_protocol
- Tumbling window: non-overlapping fixed windows. https://en.wikipedia.org/wiki/Sliding_window_protocol
- Event time vs processing time: time semantics in stream processing. https://nightlies.apache.org/flink/flink-docs-stable/docs/concepts/time/

## Usage (Specific)
- Rolling metrics (p95 latency, error rate) over last N minutes.
- Rate limiting and anomaly detection in streaming logs.
- Windowed aggregation for dashboards with near-real-time updates.

## Average Time Complexity
- Average: O(n) for one pass with window maintenance; space O(k).

## Real-World Example
- Apache Flink window operators. https://github.com/apache/flink

## Tradeoffs and Failure Modes
- Misaligned windows cause incorrect aggregations; align to event time.
- Out-of-order events require watermarking or retraction.

## LeetCode
- 239 Sliding Window Maximum
- 3 Longest Substring Without Repeating Characters

## Python Implementation
```python
def sliding_window_sum(nums, k):
    if k <= 0 or k > len(nums):
        return []
    window_sum = sum(nums[:k])
    result = [window_sum]
    for i in range(k, len(nums)):
        window_sum += nums[i] - nums[i - k]
        result.append(window_sum)
    return result
```
