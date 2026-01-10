# Token Bucket / Leaky Bucket

## Glossary
- Token bucket: tokens refilled over time, allow bursts. https://en.wikipedia.org/wiki/Token_bucket
- Leaky bucket: fixed outflow rate, smoothing bursts. https://en.wikipedia.org/wiki/Leaky_bucket
- Rate limiting: control request rate. https://en.wikipedia.org/wiki/Rate_limiting

## Usage (Specific)
- API gateway throttling with controlled burst capacity.
- Per-tenant quotas in multi-tenant services.
- Protection for expensive downstream resources.

## Average Time Complexity
- Average: O(1) per request; space O(1) per key.

## Real-World Example
- Envoy rate limit service uses token bucket models. https://github.com/envoyproxy/ratelimit

## Tradeoffs and Failure Modes
- Clock skew can break refill logic; use monotonic time.
- Per-key state can grow; apply TTL or eviction.

## LeetCode
- 359 Logger Rate Limiter
- 362 Design Hit Counter

## Python Implementation
```python
import time

class TokenBucket:
    def __init__(self, rate, capacity):
        self.rate = rate
        self.capacity = capacity
        self.tokens = capacity
        self.last = time.monotonic()

    def allow(self):
        now = time.monotonic()
        elapsed = now - self.last
        self.last = now
        self.tokens = min(self.capacity, self.tokens + elapsed * self.rate)
        if self.tokens >= 1:
            self.tokens -= 1
            return True
        return False
```
