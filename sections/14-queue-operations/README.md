# Queue Operations

## Overview
Queues implement First-In-First-Out (FIFO) behavior, supporting enqueue and dequeue operations. They're used in scheduling tasks, breadth-first search, and buffering data streams.

## Detailed Explanation
A queue adds items at the rear and removes them from the front. Both operations run in O(1) time, with space proportional to the number of elements. Array or linked list implementations are common. Stacks contrast by removing from the same end they insert.

## Code Examples
### Python
```python
from collections import deque

class Queue:
    def __init__(self):
        self.data = deque()
    def enqueue(self, item):
        self.data.append(item)
    def dequeue(self):
        return self.data.popleft()
```

```python
q = Queue()
q.enqueue(1)
q.enqueue(2)
q.dequeue()  # returns 1
```

### PHP
```php
class Queue {
    private $data = [];
    public function enqueue($item) { $this->data[] = $item; }
    public function dequeue() { return array_shift($this->data); }
}
```

```php
$q = new Queue();
$q->enqueue(1);
$q->enqueue(2);
$q->dequeue(); // returns 1
```

## Common Pitfalls & Warnings
- Dequeuing from an empty queue.
- Forgetting FIFO order when implementing.

## Best Practices
- Use circular buffers for fixed-size queues.
- PHP array_shift can be slow for large queues; consider SplQueue.

## Mini Exercise or Challenge
Create a queue and enqueue numbers 1..3, then dequeue two times. Which number remains at the front?

## Solution
---
### Python
```python
q = Queue()
for i in range(1,4):
    q.enqueue(i)
q.dequeue()
print(q.dequeue())  # returns 2
```
### PHP
```php
$q = new Queue();
for ($i=1;$i<=3;$i++) $q->enqueue($i);
$q->dequeue();
echo $q->dequeue(); // returns 2
```
