# Linked List Algorithms

## Overview
Linked lists consist of nodes where each node stores data and a reference to the next node. Algorithms include reversal, cycle detection, and merging two lists. They're fundamental in building dynamic data structures.

## Detailed Explanation
Reversing a linked list iterates through nodes, flipping their next pointers. Cycle detection uses two pointers moving at different speeds (Floyd's algorithm). Merging two sorted lists involves comparing node values one by one. Most operations run in O(n) time with O(1) additional space. Compared to arrays, linked lists have slower access but easier insertions and deletions.

## Code Examples
### Python
```python
class Node:
    def __init__(self, val):
        self.val = val
        self.next = None

# reverse linked list
 def reverse(head):
     prev = None
     current = head
     while current:
         nxt = current.next
         current.next = prev
         prev = current
         current = nxt
     return prev
```

### PHP
```php
class Node {
    public $val;
    public $next = null;
    function __construct($v) { $this->val = $v; }
}

function reverse($head) {
    $prev = null;
    $curr = $head;
    while ($curr) {
        $next = $curr->next;
        $curr->next = $prev;
        $prev = $curr;
        $curr = $next;
    }
    return $prev;
}
```

## Common Pitfalls & Warnings
- Losing track of nodes during reversal.
- Forgetting to check for null when traversing.

## Best Practices
- Draw diagrams to visualize pointer changes.
- Use dummy nodes for simplifying edge cases in merges.

## Mini Exercise or Challenge
Reverse a linked list of 1 → 2 → 3.

## Solution
---
### Python
```python
head = Node(1); head.next = Node(2); head.next.next = Node(3)
new_head = reverse(head)
print(new_head.val)  # 3
```
### PHP
```php
$head = new Node(1);
$head->next = new Node(2);
$head->next->next = new Node(3);
$new_head = reverse($head);
echo $new_head->val; // 3
```
