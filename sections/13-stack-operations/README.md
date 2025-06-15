# Stack Operations

## Overview
Stacks follow a Last-In-First-Out (LIFO) structure, allowing push and pop operations. They're essential for undo functionality, evaluating expressions, and balancing parentheses in compilers.

## Detailed Explanation
A stack maintains a pointer to the top element. Push adds to the top, pop removes from the top. Time complexity for both operations is O(1) and space depends on the number of elements. Stacks can be implemented using arrays or linked lists. Compared to queues, stacks reverse order.

## Code Examples
### Python
```python
class Stack:
    def __init__(self):
        self.data = []
    def push(self, item):
        self.data.append(item)
    def pop(self):
        return self.data.pop()
```

```python
# using list as stack
stack = []
stack.append(1)  # push
stack.append(2)
stack.pop()      # returns 2
```

### PHP
```php
class Stack {
    private $data = [];
    public function push($item) { $this->data[] = $item; }
    public function pop() { return array_pop($this->data); }
}
```

```php
$stack = new Stack();
$stack->push(1);
$stack->push(2);
$stack->pop(); // returns 2
```

## Common Pitfalls & Warnings
- Popping from an empty stack causes errors.
- Confusing LIFO with FIFO structures.

## Best Practices
- Check for empty stack before popping.
- Use arrays for speed unless huge data requires linked lists.

## Mini Exercise or Challenge
Implement a stack and push numbers 1 through 3, then pop once. What remains on top?

## Solution
---
### Python
```python
s = Stack()
for i in range(1,4):
    s.push(i)
print(s.pop())  # returns 3
```
### PHP
```php
$s = new Stack();
for ($i=1;$i<=3;$i++) $s->push($i);
echo $s->pop(); // returns 3
```
