# Exponential Moving Average (EMA)

## Glossary
- EMA: weighted average with exponentially decaying weights. https://en.wikipedia.org/wiki/Moving_average#Exponential_moving_average
- Half-life: time for weight to halve. https://en.wikipedia.org/wiki/Exponential_decay
- Smoothing factor (alpha): weight for latest value. https://en.wikipedia.org/wiki/Moving_average#Exponential_moving_average

## Usage (Specific)
- Autoscaling signals with smooth response to bursts.
- Alert thresholds for noisy metrics (CPU, latency).
- Real-time trend estimation in dashboards.

## Average Time Complexity
- Average: O(1) per update; space O(1).

## Real-World Example
- Prometheus uses EMAs in alerting and rate calculations. https://github.com/prometheus/prometheus

## Tradeoffs and Failure Modes
- Alpha too small lags behind changes; too large is noisy.
- Missing data points skew averages; handle gaps explicitly.

## LeetCode
- N/A (technique used in streaming systems)

## Python Implementation
```python
def ema(values, alpha):
    if not values:
        return []
    result = [values[0]]
    for v in values[1:]:
        result.append(alpha * v + (1 - alpha) * result[-1])
    return result
```
