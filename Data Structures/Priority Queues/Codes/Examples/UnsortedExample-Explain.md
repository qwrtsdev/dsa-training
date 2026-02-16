# Unsorted Priority Queue (Example)
This page will be used to visualize how to work around with this kind of data structure

Recommended to open a split screen between the [original file](./UnsortedExample.md) and this file.

##

```py
class UnsortedPriorityQueue():
  """A min-oriented priority queue implemented with an unsorted list."""
```

### Internal class
"Item" class is an internal class. intended for using inside **UnsortedPriorityQueue** class. (this must be remain untouched from test cases or users) 

**Note** : An underscore at the "_Item" is just a convention for telling "this is an internal class" (same as ``_key`` and ``_value``)
```py
  class _Item:
    __slots__ = '_key', '_value'
```
```__slots__``` is a special variable that creates a "template". Used for restricts what attributes you are allowed to create in the class. This variable is using along with the ``__init__`` method.

**Note** : This kind of stuff (the methods/properties that has double underscores at the beginning and the end) is something called **"dunders"**. It's a special methods/properties that includes in classes (even we're not seeing them)

It's not actively working but it'll be invoked in some actions such as when using ``+`` operator it'll invoke the method name ``__add__``. And the special part is we can create a method/property in the same name it will overwrite how it's work just like we did to these methods below
```py
    def __init__(self, k, v):
      self._key = k
      self._value = v
```
``__init__`` is what happen when we created a new classes and this will be invoked. So this will overwrite it's behavior and tell the developers to always include ``k`` (key) and ``v`` (value) when create this class and using the same template from ``__slots__``.

If not, it's will throw an error.
```py
    def __lt__(self, other):
      return self._key < other._key 
```
``__lt__`` is another dunder (of method) for this internal class (named ``_Item``). use for making comparison between the current item and other item.

And this will rewrite it's behavior to make a comparison of ``key`` when we're using ``<`` operator
```py
    def __str__(self):
      return '{}:{}'.format(self._key, self._value)
```
``__str__`` is a another dunder (of method) for this internal class (named ``_Item``). This will be invoked when using ``print(_Item)``

This will returns a string that goes like this: ``Key:Value`` (Both ``{}`` is made for replacement when using ``.format()`` method. It'll insert itself.)

### The actual class
```py
  def __init__(self):
    self._data = []
```
When we created this class. It'll transform itself into an array.

**Note** : This ``self.data`` will be use as ``self`` argument from other methods from now on.
```py
  def __str__(self):
    return '[' + ''.join([str(item) + ', ' for item in self._data]) + ']'
```
When we using ``print(UnsortedPriorityQueue)`` it returns ``[{Key1:Value1}, [{Key2:Value2}, [{Key3:Value3}]``
```py
  def __len__(self):
    return len(self._data)


  def is_empty(self):
    return len(self._data) == 0
```
``is_empty`` is user-created method of ``UnsortedPriorityQueue`` class. This using the comparison operator in short-handed way to return ``True`` or ``False``. It the length of data is equals to 0. It'll return ``True``. Otherwise, it'll return ``False``
```py
  def add(self, key, value):
    self._data.append(self._Item(key, value))
```
``add`` is user-created method that will add new data in the class's array with the use of internal ``_Item`` class (which uses the ``__slots__`` template)
```py
  def min(self):
    if self.is_empty():
      raise Exception('Priority queue is empty')

    smallest = self._data[0]

    for item in self._data:
      if item < smallest:
        smallest = item

    return smallest._key, smallest._value
```
``min`` is user-created method that will firstly runs ``.is_empty`` method to check. If ``.is_empty`` returns ``True`` it'll raise an error that says ``Priority queue is empty``

Then, it'll pick the first element in the array to be the starting point for a variable named ``smallest`` and iterates through the array and make a comparison between the current item it selected at the time with the variable named ``smallest``

As you can see, each elements in the array is the class named ``_Item`` and we already overwrite the ``<`` behavior in ``__lt__`` dunder. so it'll use the current ``_Item`` class in the array with the ``_Item`` in the variable named ``smallest`` to make a comparison between keys

If the current "key" is smaller than ``smallest`` variable's key. Then we reassign the ``smallest`` variable's value to be the same ``_Item`` class

This will be looping until we out of items in the array (in Python it's called "List" which is the same is array) and then we'll found out which one has the smallest key and return to the place this method was called with ``smallest``'s key and value.

This way it looks simple. but it takes a lot of time and resources. That's the reason why this takes time complexity as O(n). The more of items in the array, the longer it takes.
```py
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
same as the previous method but this also remove the smallest item.

## Test Cases (This is outside the class)
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
**Note** : The ``if __name__ == '__main__'`` is a common thing use in Python. When we run this python file, this script will be run which also running the methods from the classes
