# Binary Search Tree

## Overview
A binary search tree (BST) organizes nodes such that left child values are less than the parent and right child values are greater. BSTs allow efficient insertion, deletion, and searching operations, typically O(log n) when balanced.

## Detailed Explanation
Traversing a BST compares a key with the current node and follows left or right accordingly. Operations degrade to O(n) in worst case when the tree is unbalanced. Space complexity is O(n). Balanced variants like AVL or Red-Black trees maintain logarithmic height. Compared to hashmaps, BSTs keep data in order for range queries.

## Code Examples
### Python
```python
class Node:
    def __init__(self, key):
        self.key = key
        self.left = self.right = None

 def insert(root, key):
     if root is None:
         return Node(key)
     if key < root.key:
         root.left = insert(root.left, key)
     elif key > root.key:
         root.right = insert(root.right, key)
     return root

 def search(root, key):
     if root is None or root.key == key:
         return root
     if key < root.key:
         return search(root.left, key)
     return search(root.right, key)
```

### PHP
```php
class Node {
    public $key;
    public $left = null;
    public $right = null;
    function __construct($k) { $this->key = $k; }
}

function insert($root, $key) {
    if ($root === null) return new Node($key);
    if ($key < $root->key)
        $root->left = insert($root->left, $key);
    elseif ($key > $root->key)
        $root->right = insert($root->right, $key);
    return $root;
}

function search($root, $key) {
    if ($root === null || $root->key == $key) return $root;
    if ($key < $root->key) return search($root->left, $key);
    return search($root->right, $key);
}
```

## Common Pitfalls & Warnings
- Degenerates to linked list if insertions are sorted.
- Failing to balance leads to poor performance.

## Best Practices
- Keep the tree balanced using AVL or Red-Black if many inserts occur.
- In-order traversal yields sorted data.

## Mini Exercise or Challenge
Insert 5, 3, 7 into an empty BST and search for 7.

## Solution
---
### Python
```python
root = None
for v in [5,3,7]:
    root = insert(root, v)
print(search(root,7).key)  # 7
```
### PHP
```php
$root = null;
foreach ([5,3,7] as $v) $root = insert($root, $v);
$node = search($root, 7);
echo $node->key; // 7
```
