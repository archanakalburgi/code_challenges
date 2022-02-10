---
toc: false
badges: true
layout: post
description: Solution using enumerate
categories: [array, hash-table, sliding window]
title: Contains Duplicates II
date: 2022-02-08
---

# Problem statement

Given an integer array _nums_ and an integer _k_, return true if there are two distinct indices i and j in the array such that nums[i] == nums[j] and abs(i - j) <= k.

# Examples

**Input:** nums = [1,2,3,1], k = 3\
**Output:** true

**Input:** nums = [1,0,1,1], k = 1\
**Output:** true

**Input:** nums = [1,2,3,1,2,3], k = 2\
**Output:** false

## Solution 

**intuition**

- Update the dictionary key with the latest index of the number in _nums_
- The previous position of the duplicate number if less than the value _k_ : return true
- We will need the information about the previous position of a number in the input array and its current position

## Implementation 

```sh
"""
nums = [1,2,3,1], 
k = 3

k=0
1 != 2

k=1
1 != 2

k=2
1 != 3

k=3
1 == 1  -> true

brute force: two for loops
"""

class Solution:
    def containsNearbyDuplicate(self, nums, k):
        hashmap = dict()
        for i, num in enumerate(nums):
            if num in hashmap and i - hashmap[num] <= k:
                return True
            hashmap[num] = i
            
        return False
```

## Complexity 

time : O(n)\
space : O(n) 