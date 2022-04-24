---
toc: false
badges: true
layout: post
description: With O(n) time and space complexity  
title: Kth Largest Element in a Stream
categories: [array, data stream, heap, tree, binary search tree, binary search]
date: 2022-04-23
---

## Problem statement 

Design a class to find the k<sup>th</sup> largest element in a stream. Note that it is the k<sup>th</sup> largest element in the sorted order, not the k<sup>th</sup> distinct element.

Implement KthLargest class:
- **KthLargest(int k, int[ ] nums)** Initializes the object with the integer k and the stream of integers nums
- **int add (int val)** Appends the integer val to the stream and returns the element representing the kth largest element in the stream.

## Examples 

### Example 1 

**Input**\
["KthLargest", "add", "add", "add", "add", "add"]\
[[3, [4, 5, 8, 2]], [3], [5], [10], [9], [4]]\
**Output**\
[null, 4, 5, 5, 8, 8]

**Explanation**\
KthLargest kthLargest = new KthLargest (3, [4, 5, 8, 21]);\
kthLargest.add(3); // return 4\
kthLargest.add(5); / / return 5\
kthLargest.add(10); // return 5\
kthLargest.add(9); // return 8\
kthLargest.add(4); // return 8

**Constraints:**
- 1 <= k <= 10<sup>4</sup>
- 0 <= nums.length <= 10<sup>4</sup>
- -10<sup>4</sup> <= nums[i] <= 10<sup>4</sup>
- -10<sup>4</sup> <= val <= 10<sup>4</sup>
- At most 10<sup>4</sup> calls will be made to _add_.
- It is guaranteed that there will be at least _k_ elements in the array when you search for the _k<sup>th</sup>_ element.

## Implementation 

```sh
import heapq 

class KthLargest:

    def __init__(self, k, nums):
        self.num = nums
        self.k = k 
        heapq.heapify(self.num) # O(n)
        while len(self.num) > k:
            heapq.heappop(self.num) 

    def add(self, val):
        heapq.heappush(self.num, val)
        if len(self.num) > self.k: 
            heapq.heappop(self.num) 
        print(self.num[0])
        return self.num[0] 

kthLargest = KthLargest(3, [4, 5, 8, 2])
kthLargest.add(3) #   // return 4
kthLargest.add(5) #  // return 5
kthLargest.add(10)#  // return 5
kthLargest.add(9) #   // return 8
kthLargest.add(4) #   // return 8
```

## Complexity

**Time:** O(n)\
**Time:**O(n)\
Where n in the length of the input array _nums_.s