---
toc: false
badges: true
layout: post
description: Solution using two pointers 
categories: [array, two pointer, greedy]
title: Container With Most Water
date: 2022-02-06
---

# Question 

You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the i<sup>th</sup> line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water. 

Return the maximum amount of water a container can store.

**Notice** that you may not slant the container.

# Examples

**Input:** height = [1,8,6,2,5,4,8,3,7]\
**Output:** 49\
**Explanation:** The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water the container can contain is 49.

**Input:** height = [1,1]\
**Output:** 1

# Solution

```sh
"""
 0, 1, 2, 3, 4, 5, 6, 7, 8
[1, 8, 6, 2, 5, 4, 8, 3, 7]
 s                       e
 
while s<e:
    1<7 : h[s] < h[e]
        a = 1*(8-0) = 8
        s++

    8>7 : h[s] > h[e]
        a = 7*(7-0) = max(49,8) = 49
        e--

    8>3 : h[s] > h[e]
        a = 3*(7-1) = max(18,49) = 49
        e--
return a
"""
class Solution:
    def maxArea(self, height: List[int]) -> int:
        start = 0
        end = len(height)-1
        max_area=0
        while start < end:
            width = end - start
            if height[start] < height[end]:
                max_area = max(max_area, height[start]*width)
                start+=1
            else:
                max_area = max(max_area, height[end]*width)
                end-=1
        return max_area
```
