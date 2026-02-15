## About "time complexity"
- it describes how cost of "time" or "space" grows with input size (usally called "n")
- Big-O is about the "worst case" (if its happend/posible)

## Orders from "fastest" to "slowest"
O(1) -> O(log n) -> O(n) -> O(n log n) -> O(n^2) -> O(n^3) -> O(2^n) -> O(n!)

## Explaination each one
- O(n): Looping "n" times
example : for i in range(n)

- O(1): Loop with __constant work__ in each iteration

- O(n^2): Nested loops where inner runs ~n (~n is) for each outer

- O(log n): Divided problem in half each time/step

- O(n!) or O(2^n): Recursion that branches a lot (in exponential states)
