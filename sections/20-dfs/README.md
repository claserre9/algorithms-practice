# Depth-First Search (DFS)

## Overview
DFS explores a graph by going as deep as possible along each branch before backtracking. It is used in topology discovery, puzzle solving, and strongly connected components.

## Detailed Explanation
Using a stack or recursion, DFS visits a node, then iteratively visits an unvisited neighbor until none remain, then backtracks. Time complexity is O(V + E) with space O(V) for recursion or an explicit stack. Compared to BFS, DFS may use less memory but doesn't guarantee shortest paths.

## Code Examples
### Python
```python
def dfs(graph, start, visited=None, order=None):
    if visited is None:
        visited = set()
        order = []
    visited.add(start)
    order.append(start)
    for neigh in graph.get(start, []):
        if neigh not in visited:
            dfs(graph, neigh, visited, order)
    return order
```

### PHP
```php
function dfs($graph, $start, &$visited = [], &$order = []) {
    $visited[$start] = true;
    $order[] = $start;
    foreach ($graph[$start] ?? [] as $n) {
        if (!isset($visited[$n])) {
            dfs($graph, $n, $visited, $order);
        }
    }
    return $order;
}
```

## Common Pitfalls & Warnings
- Forgetting to mark nodes as visited leads to infinite recursion.
- Recursive DFS can cause stack overflow for very deep graphs.

## Best Practices
- Use iterative version for extremely deep graphs.
- DFS is great for tasks like detecting cycles or topological sorting.

## Mini Exercise or Challenge
Run DFS on `{A:[B],B:[C],C:[]}` starting at `A`.

## Solution
---
### Python
```python
graph={'A':['B'],'B':['C'],'C':[]}
print(dfs(graph,'A'))  # ['A','B','C']
```
### PHP
```php
$graph=['A'=>['B'],'B'=>['C'],'C'=>[]];
print_r(dfs($graph,'A'));
```
