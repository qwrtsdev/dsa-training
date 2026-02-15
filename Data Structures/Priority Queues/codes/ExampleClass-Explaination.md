# Example Class
this class will be used to visualize how to work around with this kind of data structure

## UnsortedPriorityQueue Class

### the class definition
```py
class UnsortedPriorityQueue():
  """A min-oriented priority queue implemented with an unsorted list."""
```

### internal class
```py
  class _Item:
    __slots__ = '_key', '_value'
```
```__slots__``` is a special variable that creates a "template"
```py
    def __init__(self, k, v):
      self._key = k
      self._value = v
```
initialize this internal class to be able to parse 2 stuff: "key" and "value" with the use of the "template"
```py
    def __lt__(self, other):
      return self._key < other._key    # compare items based on their keys
```
a function for internal class. use for making comparison between the current item and other item
```py
    def __str__(self):
      return '{}:{}'.format(self._key, self._value)
```
another function use for make a text string
Summary:
"Item" class is an internal class. intended for using inside **UnsortedPriorityQueue** class. (this must be remain untouched from test cases or users)

### the actual class
```py
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
```

## Test Cases
```py
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
when this script runs this will run the class's methods and properties
