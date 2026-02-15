# Example Class: UnsortedPriorityQueue

This example class is used to visualize how to work with a **priority queue** implemented using a simple data structure (a Python list).  
The purpose is to understand the concept, not to build the most efficient priority queue.

---

## UnsortedPriorityQueue Class

This is a **min-oriented priority queue**:
- Smaller `key` → higher priority  
- The item with the smallest key is returned first  

Internally, items are stored in an **unsorted list**.

---

## Class Definition
```py
class UnsortedPriorityQueue():
  """A min-oriented priority queue implemented with an unsorted list."""
```

Internal _Item Class

The _Item class is an internal helper class used to store (key, value) pairs inside the queue.

```py
class _Item:
  __slots__ = '_key', '_value'
```

``__slots__`` defines a fixed template for the object.
This means each _Item can only have ``_key`` and ``_value`` attributes, which saves memory and prevents mistakes.
