# Arrays and ArrayLists

## Glossary
- Array: contiguous memory for fixed-size elements. https://en.wikipedia.org/wiki/Array_(data_structure)
- Dynamic array: resizable array with amortized append. https://en.wikipedia.org/wiki/Dynamic_array
- Cache line: CPU cache unit influencing locality. https://en.wikipedia.org/wiki/CPU_cache

## Usage (Specific)
- High-throughput numeric processing (vectorized loops, SIMD-friendly layouts).
- Time-series windows and ring buffers for metrics aggregation.
- Batched IO buffers to reduce syscalls and improve throughput.

## Average Time Complexity
- Average: access O(1), append amortized O(1), insert/delete O(n).

## Real-World Example
- NumPy arrays for contiguous numeric workloads. https://github.com/numpy/numpy

## Tradeoffs and Failure Modes
- Resizing causes reallocation; pre-size when possible.
- Insert/delete in the middle is O(n) due to shifts.
- False sharing can hurt multi-threaded writes in hot loops.

## LeetCode
- 238 Product of Array Except Self
- 560 Subarray Sum Equals K
- 53 Maximum Subarray

## Python Implementation
```python
class DynamicArray:
    def __init__(self, capacity=4):
        self.capacity = capacity
        self.size = 0
        self.data = [None] * capacity

    def append(self, value):
        if self.size == self.capacity:
            self._resize(self.capacity * 2)
        self.data[self.size] = value
        self.size += 1

    def _resize(self, new_capacity):
        new_data = [None] * new_capacity
        for i in range(self.size):
            new_data[i] = self.data[i]
        self.data = new_data
        self.capacity = new_capacity

    def __getitem__(self, index):
        if index < 0 or index >= self.size:
            raise IndexError("index out of range")
        return self.data[index]
```
