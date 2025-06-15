# Hashmap Techniques

## Overview
Hashmaps store key-value pairs with near O(1) average time for insertion, deletion, and lookup. They're invaluable for frequency counts, caching, and anagram grouping.

## Detailed Explanation
A hashmap uses a hash function to map keys to indices in an array. Collisions are resolved with chaining or open addressing. Time complexity is O(1) on average but can degrade to O(n) if many collisions occur. Space complexity is proportional to the number of stored elements. Compared to arrays, hashmaps offer fast lookups by key rather than by index.

## Code Examples
### Python
```python
# frequency map example
 def char_count(s):
     freq = {}
     for ch in s:
         freq[ch] = freq.get(ch, 0) + 1
     return freq
```

### PHP
```php
function char_count($s) {
    $freq = [];
    foreach (str_split($s) as $ch) {
        if (!isset($freq[$ch])) $freq[$ch] = 0;
        $freq[$ch]++;
    }
    return $freq;
}
```

## Common Pitfalls & Warnings
- Poor hash functions lead to many collisions.
- Mutable keys that change hash values break hashmap integrity.

## Best Practices
- Use builtin dictionary or array types when possible.
- Choose good hash functions and load factors to minimize collisions.

## Mini Exercise or Challenge
Create a hashmap that counts occurrences of letters in `"hello"`.

## Solution
---
### Python
```python
print(char_count("hello"))
```
### PHP
```php
print_r(char_count("hello"));
```
