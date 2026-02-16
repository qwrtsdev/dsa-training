## Read a full explaination _[Here.](/Data%20Structures/Priority%20Queues/Codes/Examples/UnsortedExample-Explain.md)_

```py
class UnsortedPriorityQueue():
  """A min-oriented priority queue implemented with an unsorted list."""


  class _Item:
    __slots__ = '_key', '_value'

    def __init__(self, k, v):
      self._key = k
      self._value = v

    def __lt__(self, other):
      return self._key < other._key

    def __str__(self):
      return '{}:{}'.format(self._key, self._value)


  def __init__(self):
    self._data = []


  def __str__(self):
    return '[' + ''.join([str(item) + ', ' for item in self._data]) + ']'


  def __len__(self):
    return len(self._data)


  def is_empty(self):
    return len(self._data) == 0


  def add(self, key, value):
    self._data.append(self._Item(key, value))


  def min(self):
    if self.is_empty():
      raise Exception('Priority queue is empty')

    smallest = self._data[0]

    for item in self._data:
      if item < smallest:
        smallest = item

    return smallest._key, smallest._value


  def remove_min(self):
    if self.is_empty():
      raise Exception('Priority queue is empty')

    smallest = self._data[0]

    for item in self._data:
      if item < smallest:
        smallest = item

    self._data.remove(smallest)
    return smallest._key, smallest._value




if __name__ == '__main__':
  pq = UnsortedPriorityQueue()
  pq.add(2, 'two')
  pq.add(1, 'one')
  pq.add(4, 'four')
  pq.add(3, 'three')
  print(pq)
  print(pq.min())
  print(pq.remove_min())
```
