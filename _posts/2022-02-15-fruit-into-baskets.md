---
toc: false
badges: true
layout: post
description: Sliding window problem, understanding invariance 
categories: [sliding window, invariance, hashmap, array]
title: Fruit Into Baskets
date: 2022-02-15
---

## Problem

You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array fruits where fruits[i] is the **type** of fruit the i<sup>th</sup> tree produces.

You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:
- You only have **two** baskets, and each basket can only hold a **single type** of fruit. There is no limit on the amount of fruit each basket can hold.
- Starting from any tree of your choice, you must pick **exactly one fruit** from **every** tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.
- Once you reach a tree with fruit that cannot fit in your baskets, you must stop.

Given the integer array fruits, return the **maximum** number of fruits you can pick.

## Examples 

### Example1

**Input :** fruits = [1,2,1]\
**Output :** 3\
**Explanation :** We can pick from all 3 trees.

### Example2

**Input :** fruits = [0,1,2,2]\
**Output :** 3\
**Explanation :** We can pick from trees [1,2,2].\
If we had started at the first tree, we would only pick from trees [0,1].

### Example3

**Input :** [1,2,3,2,2]\
**Output :** 4\
**Explanation :** We can pick from trees [2,3,2,2].\
If we had started at the first tree, we would only pick from trees [1,2].

## Constraints:
- 1 <= fruits. length <= 10<sup>5</sup>
- 0 <= fruits[i] < fruits.length

## Solution

```sh
import collections

class Solution:
    def totalFruit(self, fruits: List[int]) -> int:
        
        basket = collections.defaultdict(int)
        start = 0
        max_fruits = 0
        
        for i in range(len(fruits)):
            basket[fruits[i]] += 1
            
            if len(basket) > 2:
                basket[fruits[start]] -= 1
                
                if basket[fruits[start]] == 0:
                    del basket[fruits[start]]
                
                start += 1
            
            max_fruits = max(max_fruits, (i-start+1))
        
        return max_fruits 
```

## Complexity 

- **Time :** O(n)
- **Space :** O(1)