---
toc: false
badges: true
layout: post
description: Solution using hashmap 
categories: [string, hashtable]
title: Find the difference
date: 2022-02-07
---

## Problem statement

You are given two strings _s_ and _t_. String _t_ is generated by random shuffling string _s_ and then add one more letter at a random position.

Return the letter that was added to _t_.

## Example

**input:** s = "abcd", t = "abcde"
**output:** "e"
**Explanation:** 'e' is the letter that was added.

**input:** s = "", t = "y"
**output:** "y"

## Solution 
 
```sh
"""
s=abcd
t=dabce

{a,b,c,d}
iterate t 
    d in {a,b,c,d}
    a in {a,b,c,d}
    b in {a,b,c,d}
    c in {a,b,c,d}
    e not in {a,b,c,d}
        return e
"""
import collections
class Solution:
    def findTheDifference(self, s: str, t: str) -> str:
        if s == "":
            return t
        
        s_set = collections.Counter(s)
            
        for tt in t:
            if tt in s_set:
                if s_set[tt] > 0:
                    s_set[tt] -= 1
                else:
                    return tt

            if tt not in s_set:
                return tt
        
        return ""
```

