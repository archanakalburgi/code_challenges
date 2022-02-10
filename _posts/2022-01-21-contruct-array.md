---
toc: false
badges: true
layout: post
description: Problem breakdown 
categories: [array_construction]
title: Calculate a boolean array 
date: 2022-01-21
---

## Question 

You are given an array of integers a and two integers l and r. You task is to calculate a boolean array b, where b[i] = true if there exists an integer x, such that a[i] = (i + 1) * x and l<= x <= r. Otherwise, b[i] should be set to false

## Example

For a = [8, 5, 6, 16, 51], l = 1, and r = 3, the output should be solution (a, l, r) = [false, false, true, false, true].
- For a[0] = 8 , we need to find a value of x such that 1 * x = 8, but the only value that would work is x = 8 which doesn't satisfy the boundaries 1 <= x <= 3, so b[0] = false.
- For a[1] = 5, we need to find a value of x such that 2 * x = 5, but there is no integer value that would satisfy this equation, so b[1] = false
- For a[2] = 6, we can choose x because 3 * 2 = 6 and 1 <= 2 <= 3, so b[2] = true
- For a[3] = 16, there is no an integer 1 <= x <= 3 , such that 4 * x = 16, so b[3] = false.
- For a[4] = 5, we can choose x = 1 because 5 * 1 = 5 and 1 <= 1 <= 3 , so b[4] = true.


## Guaranteed constraints:

- 1 <= a.length <= 100
- 1 <= a[i] <= 10^6
- 1 <= l <= 10^4
- 1 <= r <= 10^4

## Pseudocode

```sh
func (i, a[i], l, r):
    for x in range(l, r+1):
        if (i+1)*x == a[i]:
            return true
    return false

main()
    iterate a
        fun (i,ali], l,r)-> t
            b=> append bool
    return b
```

## Implementation

```sh
def helper (i, num, l, r):
    for in range(l, r+1):
        if (i+1)*x == num:
            return True
    return False

def solution(a, l, r):
    b = list()
    for i in range(len(a)):
        res = helper(i, a[i], l, r)
        b.append(res)
    return b
```
