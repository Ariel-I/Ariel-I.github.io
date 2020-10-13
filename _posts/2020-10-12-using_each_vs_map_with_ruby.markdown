---
layout: post
title:      "Using each VS map (with Ruby)"
date:       2020-10-12 19:45:35 -0400
permalink:  using_each_vs_map_with_ruby
---


**EACH VS MAP ** 

Understanding the difference between .each VS .map and when to use them. 

Each and map are methods in ruby used with hashes, ranges, and arrays. They both return data.

map is also referred to as .collect. They do the same thing!

Map and each are similar methods but understanding the difference is key to knowing when to use ‘each’ and when to use ‘map’. Both are methods, that when used iterate through the given data (arrays, hashes etc.) and return the value of the each/map block that was set. 

For example;

**Using each:**


```
array =  [1, 2, 3]

array.each { | i | i * 2 }
```
This will return [1, 2, 3]

The each iterator will return the same, **original**, array.

**Using map:**


```
array = [1, 2, 3]

array.map { | i | i * 2 }
```

This will return [2, 4, 6] a changed array!

The map iterator has a **different** return value than the original array.  


