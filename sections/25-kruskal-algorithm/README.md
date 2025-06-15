# Kruskal Algorithm

## Overview
Kruskal's algorithm builds a minimum spanning tree (MST) by choosing edges in increasing weight order that don't create cycles. It's used in network design and clustering.

## Detailed Explanation
Sort edges by weight, then iterate through them, adding an edge to the MST if it connects two previously disconnected components, tracked using a disjoint set (union-find). Time complexity is O(E log E) due to sorting. Compared to Prim's algorithm, Kruskal works well on sparse graphs.

## Code Examples
### Python
```python
class DisjointSet:
    def __init__(self, n):
        self.parent=list(range(n))
    def find(self, x):
        if self.parent[x]!=x:
            self.parent[x]=self.find(self.parent[x])
        return self.parent[x]
    def union(self, a,b):
        pa,pb=self.find(a),self.find(b)
        if pa!=pb:
            self.parent[pb]=pa

def kruskal(n, edges):
    edges.sort(key=lambda x: x[2])
    ds=DisjointSet(n)
    mst=[]
    for u,v,w in edges:
        if ds.find(u)!=ds.find(v):
            ds.union(u,v)
            mst.append((u,v,w))
    return mst
```

### PHP
```php
class DisjointSet {
    public $parent;
    function __construct($n){$this->parent=range(0,$n-1);}    
    function find($x){
        if ($this->parent[$x]!=$x) $this->parent[$x]=$this->find($this->parent[$x]);
        return $this->parent[$x];
    }
    function union($a,$b){
        $pa=$this->find($a);$pb=$this->find($b);
        if($pa!=$pb)$this->parent[$pb]=$pa;
    }
}

function kruskal($n,$edges){
    usort($edges,function($a,$b){return $a[2]<=>$b[2];});
    $ds=new DisjointSet($n);
    $mst=[];
    foreach($edges as [$u,$v,$w]){
        if($ds->find($u)!=$ds->find($v)){
            $ds->union($u,$v);
            $mst[]=[$u,$v,$w];
        }
    }
    return $mst;
}
```

## Common Pitfalls & Warnings
- Forgetting to sort edges correctly.
- Not using path compression in union-find, leading to slow operations.

## Best Practices
- Use union-find with path compression for efficiency.
- Suitable for sparse graphs with many vertices.

## Mini Exercise or Challenge
Find the MST of 3 nodes with edges (0,1,1), (1,2,2), (0,2,3).

## Solution
---
### Python
```python
edges=[(0,1,1),(1,2,2),(0,2,3)]
print(kruskal(3,edges))  # [(0,1,1),(1,2,2)]
```
### PHP
```php
$edges=[[0,1,1],[1,2,2],[0,2,3]];
print_r(kruskal(3,$edges));
```
