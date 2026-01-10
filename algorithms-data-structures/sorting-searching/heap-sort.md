# Heap Sort

## Glossary
- Binary heap: complete binary tree with heap property. https://en.wikipedia.org/wiki/Binary_heap
- Heapify: build heap in O(n). https://en.wikipedia.org/wiki/Heapsort#Heapify
- In-place algorithm: uses O(1) extra memory. https://en.wikipedia.org/wiki/In-place_algorithm

## Usage (Specific)
- In-place sorting for memory-constrained systems (embedded, large in-memory arrays).
- Sorting data where worst-case O(n log n) is required and stability is not.
- Partial sorting by extracting top-k elements from the heap.

## Average Time Complexity
- Average: O(n log n); space O(1).

## Real-World Example
- C++ `std::sort_heap` uses heap sort mechanics. https://github.com/llvm/llvm-project/blob/main/libcxx/include/__algorithm/sort_heap.h

## Tradeoffs and Failure Modes
- Poor cache locality compared to quick/merge sort.
- Not stable.
- Generally slower in practice for large in-memory sorts.

## LeetCode
- 215 Kth Largest Element in an Array (heap-based approach)
- 347 Top K Frequent Elements
- 703 Kth Largest Element in a Stream

## Python Implementation
```python
def heap_sort(arr):
    n = len(arr)

    def heapify(n, i):
        largest = i
        left = 2 * i + 1
        right = 2 * i + 2
        if left < n and arr[left] > arr[largest]:
            largest = left
        if right < n and arr[right] > arr[largest]:
            largest = right
        if largest != i:
            arr[i], arr[largest] = arr[largest], arr[i]
            heapify(n, largest)

    for i in range(n // 2 - 1, -1, -1):
        heapify(n, i)

    for i in range(n - 1, 0, -1):
        arr[0], arr[i] = arr[i], arr[0]
        heapify(i, 0)

    return arr
```
