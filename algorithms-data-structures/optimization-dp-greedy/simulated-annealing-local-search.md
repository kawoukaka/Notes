# Simulated Annealing / Local Search

## Glossary
- Simulated annealing: probabilistic optimization with temperature schedule. https://en.wikipedia.org/wiki/Simulated_annealing
- Local search: improve solutions by local moves. https://en.wikipedia.org/wiki/Local_search_(optimization)
- Cooling schedule: controls acceptance probability. https://en.wikipedia.org/wiki/Simulated_annealing#Cooling_schedule

## Usage (Specific)
- Large combinatorial optimization (routing, packing) where exact methods are too slow.
- Feature selection for ML with expensive evaluation.
- Layout optimization (UI widgets, warehouse slots) with many constraints.

## Average Time Complexity
- Average: O(iterations * cost(energy + neighbor)).

## Real-World Example
- OR-Tools uses local search for vehicle routing. https://github.com/google/or-tools

## Tradeoffs and Failure Modes
- No optimality guarantee; results depend on schedule and initialization.
- Poor cooling schedule can trap in local minima.
- Needs domain-specific neighborhood design for good solutions.

## LeetCode
- N/A (typically used in production optimizers, not coding interviews)

## Python Implementation
```python
import math
import random

def simulated_annealing(initial, energy, neighbor, temp=100.0, cooling=0.95, steps=1000):
    current = initial
    best = current
    for _ in range(steps):
        t = temp
        candidate = neighbor(current)
        delta = energy(candidate) - energy(current)
        if delta < 0 or random.random() < math.exp(-delta / max(t, 1e-9)):
            current = candidate
            if energy(current) < energy(best):
                best = current
        temp *= cooling
    return best
```
