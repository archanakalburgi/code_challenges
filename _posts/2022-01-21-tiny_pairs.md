---
toc: false
badges: true
layout: post
description: Problem breakdown 
categories: [array, tiny_pairs]
title: Number of tiny pairs 
date: 2022-01-21
---

## Problem 

You are given two arrays of integers and b of the same length, and an integer k. We will be iterating through array a from left to right, and simultaneously through array b from right to left, and looking at pairs (x, y) where x is from a and y is from b. Such pair is called _tiny_ if the concatenation xy is strictly less than k

Your task is to return the number of tiny pairs that you'll encounter during the simultaneous iteration through a and b.

## Example

### Example 1 

For [1, 2, 3] b = (1, 2, 3) and k = 31 , the output should be solution(a, b, k) = 2

We're considering the following pairs during iteration:
- (1, 3) : Their concatenation equals 13, which is less than 31 SO the pair iS tiny;
- (2 2)  : Their concatenation equals 22 , which is less than 31 so the IS pair is tiny;
- (3, 1) : Their concatenation equals 31 which is not less than 31 so the pair is not tiny.

As you can see, there are 2 tiny pairs during the iteration, so the answer is 2.

### Example 2

For a[16, 14] , b = [7, 11, 2, 15] , and k = 743 , the output should be solution (a, b, k) = 4

We're considering the Following pairs during iteration:
- (16, 15) : Their concatenation equals 1615 , which is greater than 743, so the pair is not tiny;
- (1, 0) : Their concatenation equals 10 , which is less than 743, so the pair is tiny;
- (4, 2) : Their concatenation equals 42 , which is less than 743, so the pair is tiny.
- (2, 11) : Their concatenation equals 211 , which is less than 743, so the pair is tiny;
- (14, 7) : Their concatenation equals 147 which is less than 743 , so the pair is tiny.

There are 4 tiny pairs during the iteration. So the answer is 4

## Pseudocode

```sh
fun (a[i], b[j], k)
    str_a = str(a[i])
    str_b = srt(b[i])
    res_str = str_a + str_b
    return int(res_str) < k

main()
    i=0, j=len (b) =1
    while i<len(a) and j<=0:
        if fun(a[i], b[i], k):
            count++
        i+=1, j-=1
    return count
```

## Implementation

```sh
def helper(a, b, k):
    str_a = str(a)
    str_b = str(b)
    res_str = str_a + str_b
    return int(res str) < k

def solution(a, b, k):
    i = 0
    j = len(b)-1
    count = 0
    while i<len(a) and j>=0:
        if helper(a[i], b[j], k):
            count = count+1
        i+=1
        j-=1
    return count
```