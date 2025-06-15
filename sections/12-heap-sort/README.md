# Heap Sort

## Overview
Heap sort converts the array into a binary heap and repeatedly extracts the maximum (or minimum) to produce a sorted list. It guarantees O(n log n) time and works in place without additional arrays.

## Detailed Explanation
First, heapify the array into a max heap. Then swap the first and last elements, reduce the heap size, and heapify again. Repeat until the array is sorted. Both heap creation and each extraction take O(log n), leading to O(n log n) time and O(1) space. Compared with quick sort, heap sort offers better worst-case bounds but typically has worse cache performance.

## Code Examples
### Python
```python
import heapq

def heap_sort(arr):
    heapq.heapify(arr)
    return [heapq.heappop(arr) for _ in range(len(arr))]
```

```python
# manual heap sort using max heap
 def heap_sort_manual(arr):
     n = len(arr)
     for i in range(n//2 - 1, -1, -1):
         sift_down(arr, i, n)
     for end in range(n - 1, 0, -1):
         arr[0], arr[end] = arr[end], arr[0]
         sift_down(arr, 0, end)

 def sift_down(heap, start, end):
     root = start
     while True:
         child = 2 * root + 1
         if child >= end:
             break
         if child + 1 < end and heap[child] < heap[child + 1]:
             child += 1
         if heap[root] < heap[child]:
             heap[root], heap[child] = heap[child], heap[root]
             root = child
         else:
             break
```

### PHP
```php
function heap_sort($arr) {
    $heap = new SplMinHeap();
    foreach ($arr as $v) $heap->insert($v);
    $result = [];
    while (!$heap->isEmpty()) {
        $result[] = $heap->extract();
    }
    return $result;
}
```

```php
// manual max heap implementation
function heap_sort_manual(&$arr) {
    $n = count($arr);
    for ($i = intdiv($n, 2) - 1; $i >= 0; $i--) {
        sift_down($arr, $i, $n);
    }
    for ($end = $n - 1; $end > 0; $end--) {
        [$arr[0], $arr[$end]] = [$arr[$end], $arr[0]];
        sift_down($arr, 0, $end);
    }
}

function sift_down(&$heap, $start, $end) {
    $root = $start;
    while (true) {
        $child = 2 * $root + 1;
        if ($child >= $end) break;
        if ($child + 1 < $end && $heap[$child] < $heap[$child+1]) {
            $child++;
        }
        if ($heap[$root] < $heap[$child]) {
            [$heap[$root], $heap[$child]] = [$heap[$child], $heap[$root]];
            $root = $child;
        } else {
            break;
        }
    }
}
```

## Common Pitfalls & Warnings
- Forgetting to re-heapify after each extraction.
- Using min heap vs max heap incorrectly for the desired order.

## Best Practices
- Effective when consistent O(n log n) is required.
- Not stable; use another sort if stability is needed.

## Mini Exercise or Challenge
Sort `[4,1,3,2]` with heap sort.

## Solution
---
### Python
```python
print(heap_sort([4,1,3,2]))  # [1,2,3,4]
```
### PHP
```php
print_r(heap_sort([4,1,3,2]));
```
