# Topological Sort

## Overview
Topological sort orders the vertices of a directed acyclic graph (DAG) so that for every directed edge u → v, u comes before v. It's used in scheduling tasks with dependencies and resolving build order.

## Detailed Explanation
Kahn's algorithm repeatedly removes nodes with zero in-degree, while DFS-based ordering pushes nodes onto a stack after exploring neighbors. Time complexity is O(V + E). Topological sort is impossible if the graph contains cycles. Compared to BFS or DFS alone, it ensures dependency order.

## Code Examples
### Python
```python
from collections import deque

def topo_sort(graph):
    indeg = {v:0 for v in graph}
    for nodes in graph.values():
        for n in nodes:
            indeg[n] += 1
    q = deque([v for v in graph if indeg[v]==0])
    order = []
    while q:
        v = q.popleft()
        order.append(v)
        for n in graph[v]:
            indeg[n]-=1
            if indeg[n]==0:
                q.append(n)
    return order
```

### PHP
```php
function topo_sort($graph) {
    $indeg = [];
    foreach ($graph as $v => $edges) {
        if (!isset($indeg[$v])) $indeg[$v]=0;
        foreach ($edges as $n) {
            $indeg[$n] = ($indeg[$n] ?? 0) + 1;
        }
    }
    $queue = [];
    foreach ($indeg as $v=>$d) if ($d==0) $queue[]=$v;
    $order = [];
    while ($queue) {
        $v = array_shift($queue);
        $order[] = $v;
        foreach ($graph[$v] as $n) {
            $indeg[$n]--;
            if ($indeg[$n]==0) $queue[]=$n;
        }
    }
    return $order;
}
```

## Common Pitfalls & Warnings
- Forgetting to handle cycles which make topological ordering impossible.
- Incorrect in-degree initialization.

## Best Practices
- Verify the graph is a DAG before performing topological sort.
- Use adjacency lists for efficiency.

## Mini Exercise or Challenge
Topologically sort graph `{A:[B],B:[C],C:[]}`.

## Solution
---
### Python
```python
graph={'A':['B'],'B':['C'],'C':[]}
print(topo_sort(graph))  # ['A','B','C']
```
### PHP
```php
$graph=['A'=>['B'],'B'=>['C'],'C'=>[]];
print_r(topo_sort($graph));
```
