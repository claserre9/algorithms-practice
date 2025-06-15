# Graph Representation

## Overview
Graphs can be represented using adjacency lists or adjacency matrices. Choice of representation affects memory usage and algorithm efficiency. Graphs model networks, dependencies, and social connections.

## Detailed Explanation
An adjacency list stores for each vertex the list of its neighbors, requiring O(V + E) space. An adjacency matrix uses a 2D array, requiring O(V^2) space but enabling O(1) edge checks. Sparse graphs favor adjacency lists, while dense graphs may use matrices. Compared to edge lists, these structures allow faster queries.

## Code Examples
### Python
```python
# adjacency list using dict
graph = {
    'A': ['B', 'C'],
    'B': ['C'],
    'C': ['A']
}

# adjacency matrix
matrix = [[0,1,1],[0,0,1],[1,0,0]]
```

### PHP
```php
// adjacency list
$graph = [
    'A' => ['B','C'],
    'B' => ['C'],
    'C' => ['A']
];

// adjacency matrix
$matrix = [
    [0,1,1],
    [0,0,1],
    [1,0,0]
];
```

## Common Pitfalls & Warnings
- Using an adjacency matrix for very large sparse graphs wastes memory.
- Forgetting to create entries for nodes without edges.

## Best Practices
- Choose representation based on graph density and algorithm requirements.
- Keep edges consistent in both directions for undirected graphs.

## Mini Exercise or Challenge
Represent a triangle graph (3 fully connected nodes) using both methods.

## Solution
---
### Python
```python
triangle_list = {0:[1,2],1:[0,2],2:[0,1]}
triangle_matrix = [[0,1,1],[1,0,1],[1,1,0]]
```
### PHP
```php
$triangle_list = [0=>[1,2],1=>[0,2],2=>[0,1]];
$triangle_matrix = [
    [0,1,1],
    [1,0,1],
    [1,1,0]
];
```
