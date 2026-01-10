# Roaring Bitmaps

## Glossary
- Bitmap: bitset for membership. https://en.wikipedia.org/wiki/Bit_array
- Roaring bitmap: compressed bitmap with containers. https://roaringbitmap.org/
- Container: array/bitmap/run-length encoding chunk. https://roaringbitmap.org/about/

## Usage (Specific)
- Fast set intersections for analytics filters (user segments, feature targeting).
- Access control list checks with large user-id sets.
- Query acceleration in columnar analytics.

## Average Time Complexity
- Average: contains O(1); union/intersection proportional to container count.

## Real-World Example
- RoaringBitmap Java implementation. https://github.com/RoaringBitmap/RoaringBitmap

## Tradeoffs and Failure Modes
- Best for dense or clustered integer IDs; less effective on sparse random keys.
- Requires integer keys; not for arbitrary objects without mapping.
- Compression ratios vary with data distribution.

## LeetCode
- N/A (typically used in analytics systems rather than coding interviews)

## Python Implementation
```python
# Simple bitmap approach for demonstration; real roaring needs containerization.
class BitMap:
    def __init__(self):
        self.bits = 0

    def add(self, value):
        if value < 0:
            raise ValueError("value must be non-negative")
        self.bits |= 1 << value

    def contains(self, value):
        return (self.bits & (1 << value)) != 0
```
