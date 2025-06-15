# Dijkstra Algorithm

## Overview
Dijkstra's algorithm finds the shortest paths from a source node to all other nodes in a graph with non-negative edge weights. It's widely used in routing and navigation systems.

## Detailed Explanation
Using a priority queue, the algorithm repeatedly selects the vertex with the smallest tentative distance and relaxes its outgoing edges. Once a vertex is visited, the shortest distance to it is finalized. Time complexity is O((V + E) log V) with a binary heap. Compared with Bellman-Ford, Dijkstra is faster but doesn't handle negative weights.

## Code Examples
### Python
```python
import heapq

def dijkstra(graph, start):
    dist = {v: float('inf') for v in graph}
    dist[start] = 0
    pq = [(0, start)]
    while pq:
        d, v = heapq.heappop(pq)
        if d > dist[v]:
            continue
        for w, weight in graph[v]:
            nd = dist[v] + weight
            if nd < dist[w]:
                dist[w] = nd
                heapq.heappush(pq, (nd, w))
    return dist
```

### PHP
```php
function dijkstra($graph, $start) {
    $dist = [];
    foreach ($graph as $v => $_) $dist[$v] = INF;
    $dist[$start] = 0;
    $pq = new SplPriorityQueue();
    $pq->setExtractFlags(SplPriorityQueue::EXTR_BOTH);
    $pq->insert($start, 0);
    while (!$pq->isEmpty()) {
        $cur = $pq->extract();
        $v = $cur['data'];
        $d = -$cur['priority'];
        if ($d > $dist[$v]) continue;
        foreach ($graph[$v] as [$w, $weight]) {
            $nd = $dist[$v] + $weight;
            if ($nd < $dist[$w]) {
                $dist[$w] = $nd;
                $pq->insert($w, -$nd);
            }
        }
    }
    return $dist;
}
```

## Common Pitfalls & Warnings
- Using Dijkstra with negative edges yields incorrect paths.
- Not updating the priority queue when distances decrease.

## Best Practices
- Suitable for graphs with non-negative weights.
- Use Fibonacci heaps or optimized structures for very dense graphs.

## Mini Exercise or Challenge
Find shortest paths from `A` in graph `{A:[('B',1),('C',4)],B:[('C',2)],C:[]}`.

## Solution
---
### Python
```python
graph={'A':[('B',1),('C',4)],'B':[('C',2)],'C':[]}
print(dijkstra(graph,'A'))
```
### PHP
```php
$graph=['A'=>[['B',1],['C',4]],'B'=>[['C',2]],'C'=>[]];
print_r(dijkstra($graph,'A'));
```
