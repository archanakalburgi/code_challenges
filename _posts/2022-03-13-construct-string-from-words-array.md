---
toc: false
badges: true
layout: post
description: Construct a string from a given array of words
title: String from an array of words
categories: [string, array]
date: 2022-03-13
---

## Problem statement 

You are given an array of strings **arr**. Your task is to construct a string from the words in **arr** starting with the **0<sup>th</sup>** character from each word (in the order they appear in **arr**), followed by the **1<sup>th</sup>** character, then the **2<sup>th</sup>** character, etc. If one of the words doesn't have an **i<sup>th</sup>** character, skip that word.

Return the resulting string.


## Example 

1. For **arr = ["Daisy", "Rose", "Hyacinth", "Poppy"]**, the output should be **solution(arr) = "DRHPaoyoisapsecpyiynth"**

First, we append all **0<sup>th</sup>** characters and obtain string **"DRHP"**
- Then we append all **1<sup>th</sup>** characters and obtain string **"DRHPaoyo"**
- Then we append all **2<sup>th</sup>** characters and obtain string **"DRHPaoyoisap"**
- Then we append all **3<sup>rd</sup>** characters and obtain string **"DRHPaoyoisapaecp"**
- Then we append all **4<sup>th</sup>** characters and obtain string **"DRHPaoyoisapaecpyiy"**
- Finally, only letters in the **arr[2]** are left, so we append the rest characters and get **"DRHPaoyoisapaecpyiynth"**


2. For **arr = ["E", "M", "I", "L", "Y"]** the output should be **solution(arr) "EMILY"**       

- Since each of these strings have only one character, the answer will be concatenation of each string in order, so the answer is **EMILY**


## Input/Output

_Guaranteed constraints:_
1 ≤ arr.length ≤ 100 
1 ≤ arr[i].length < 100 

**[execution time limit] 4 seconds (py3)**
**[input] array string arr**

An array of strings containing alphanumeric characters.

**[output] string**

Return the resulting string.


## Implementation 

```sh
def helper(arr, i, temp=""):
    for word in arr:
        if i < len(word):
            temp += word[i]
        else:
            continue
    return temp

def solution(arr):
    result_string = ""
    i = 0
    max_len = 0

    for word in arr:
        if len(word) > max_len:
            max_len = len(word)
    
    for wrd in arr:
        while i<max_len:
            result_string += helper(arr,i)
            i += 1
    
    return result_string
```