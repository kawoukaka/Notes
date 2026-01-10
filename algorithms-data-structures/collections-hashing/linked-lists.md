# Linked Lists

## Glossary
- Singly linked list: nodes with next pointers. https://en.wikipedia.org/wiki/Linked_list
- Doubly linked list: nodes with prev/next pointers. https://en.wikipedia.org/wiki/Doubly_linked_list
- Intrusive list: payload embeds link pointers. https://en.wikipedia.org/wiki/Intrusive_list

## Usage (Specific)
- LRU caches where O(1) delete/move is needed with stable iterators.
- Memory-constrained systems that benefit from node pooling or reuse.
- Implementing adjacency lists for graph algorithms.

## Average Time Complexity
- Average: search O(n), insert/delete O(1) with node pointer.

## Real-World Example
- Linux kernel list implementation (intrusive). https://github.com/torvalds/linux/blob/master/include/linux/list.h

## Tradeoffs and Failure Modes
- Poor cache locality; pointer chasing is slow.
- Memory overhead per node is high.
- Concurrency requires careful locking or lock-free structures.

## LeetCode
- 206 Reverse Linked List
- 21 Merge Two Sorted Lists
- 146 LRU Cache

## Python Implementation
```python
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None

class SinglyLinkedList:
    def __init__(self):
        self.head = None

    def push_front(self, value):
        node = Node(value)
        node.next = self.head
        self.head = node

    def remove(self, value):
        prev = None
        cur = self.head
        while cur:
            if cur.value == value:
                if prev:
                    prev.next = cur.next
                else:
                    self.head = cur.next
                return True
            prev = cur
            cur = cur.next
        return False
```
