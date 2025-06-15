# Bellman-Ford Algorithm

## Overview
The Bellman-Ford algorithm computes shortest paths from a source node in a graph that may contain negative edge weights. It detects negative cycles and is used in routing protocols.

## Detailed Explanation
Relax each edge V−1 times. If a further relaxation is possible, a negative cycle exists. Time complexity is O(VE) and space is O(V). Compared to Dijkstra, Bellman-Ford is slower but handles negative weights and cycle detection.

## Code Examples
### Python
```python
def bellman_ford(graph, start):
    dist = {v: float('inf') for v in graph}
    dist[start] = 0
    for _ in range(len(graph)-1):
        for u in graph:
            for v, w in graph[u]:
                if dist[u] + w < dist[v]:
                    dist[v] = dist[u] + w
    for u in graph:
        for v, w in graph[u]:
            if dist[u] + w < dist[v]:
                raise ValueError('Negative cycle')
    return dist
```

### PHP
```php
function bellman_ford($graph, $start) {
    $dist = [];
    foreach ($graph as $v => $_) $dist[$v] = INF;
    $dist[$start] = 0;
    $vcount = count($graph);
    for ($i=0;$i<$vcount-1;$i++) {
        foreach ($graph as $u=>$edges) {
            foreach ($edges as [$v,$w]) {
                if ($dist[$u]+$w < $dist[$v])
                    $dist[$v] = $dist[$u]+$w;
            }
        }
    }
    foreach ($graph as $u=>$edges) {
        foreach ($edges as [$v,$w]) {
            if ($dist[$u]+$w < $dist[$v])
                throw new Exception('Negative cycle');
        }
    }
    return $dist;
}
```

## Common Pitfalls & Warnings
- Failing to detect negative cycles.
- Running unnecessarily on graphs without negative edges (slower than Dijkstra).

## Best Practices
- Use when negative edges may be present.
- Optimize by stopping early if no changes occur in a pass.

## Mini Exercise or Challenge
Compute shortest paths from `A` in graph `{A:[('B',1)],B:[('C',-2)],C:[]}`.

## Solution
---
### Python
```python
graph={'A':[('B',1)],'B':[('C',-2)],'C':[]}
print(bellman_ford(graph,'A'))
```
### PHP
```php
$graph=['A'=>[['B',1]],'B'=>[['C',-2]],'C'=>[]];
print_r(bellman_ford($graph,'A'));
```
