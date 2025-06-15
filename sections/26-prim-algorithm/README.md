# Prim Algorithm

## Overview
Prim's algorithm constructs a minimum spanning tree by starting from an arbitrary node and repeatedly adding the cheapest edge that connects a vertex inside the tree to one outside. It's useful in networking and designing road systems.

## Detailed Explanation
Maintain a priority queue of edges that cross the cut between tree vertices and others. Each step selects the minimal edge and expands the tree. Time complexity is O(E log V) with a binary heap. Compared to Kruskal, Prim works well on dense graphs.

## Code Examples
### Python
```python
import heapq

def prim(graph, start=0):
    visited = set([start])
    edges = [(w, start, v) for v, w in graph[start]]
    heapq.heapify(edges)
    mst = []
    while edges:
        w, u, v = heapq.heappop(edges)
        if v not in visited:
            visited.add(v)
            mst.append((u, v, w))
            for to, weight in graph[v]:
                if to not in visited:
                    heapq.heappush(edges, (weight, v, to))
    return mst
```

### PHP
```php
function prim($graph, $start=0) {
    $visited = [$start=>true];
    $edges = new SplPriorityQueue();
    foreach ($graph[$start] as [$v,$w]) $edges->insert([$start,$v,$w], -$w);
    $mst = [];
    while (!$edges->isEmpty()) {
        [$u,$v,$w] = $edges->extract();
        if (!isset($visited[$v])) {
            $visited[$v] = true;
            $mst[] = [$u,$v,$w];
            foreach ($graph[$v] as [$to,$weight]) {
                if (!isset($visited[$to]))
                    $edges->insert([$v,$to,$weight], -$weight);
            }
        }
    }
    return $mst;
}
```

## Common Pitfalls & Warnings
- Not tracking visited nodes can create cycles.
- Priority queue implementation must support decrease key or equivalent.

## Best Practices
- Works well on dense graphs.
- Use Fibonacci heaps for theoretical improvements on very large graphs.

## Mini Exercise or Challenge
Compute an MST starting at 0 for graph `{0:[(1,1),(2,3)],1:[(2,1)],2:[]}`.

## Solution
---
### Python
```python
graph={0:[(1,1),(2,3)],1:[(2,1)],2:[]}
print(prim(graph,0))  # [(0,1,1),(1,2,1)]
```
### PHP
```php
$graph=[0=>[[1,1],[2,3]],1=>[[2,1]],2=>[]];
print_r(prim($graph,0));
```
