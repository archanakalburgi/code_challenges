---
toc: true
badges: true
layout: post
description: Solution using hashmap 
categories: [markdown]
title: Find and Replace Pattern
date: 2022-01-18
---

### Problem statements

Given a list of strings words and a string pattern, return a list of words[i] that match pattern. You may return the answer in any order.

A word matches the pattern if there exists a permutation of letters p so that after replacing every letter x in the pattern with p(x), we get the desired word.

Recall that a permutation of letters is a bijection from letters to letters: every letter maps to another letter, and no two letters map to the same letter.

#### Examples 

Example 1:

Input: words = ["abc","deq","mee","aqq","dkd","ccc"], pattern = "abb"\
Output: ["mee","aqq"]\
Explanation: "mee" matches the pattern because there is a permutation {a -> m, b -> e, ...}. 
"ccc" does not match the pattern because {a -> c, b -> c, ...} is not a permutation, since a and b map to the same letter.

Example 2:

Input: words = ["a","b","c"], pattern = "a" \
Output: ["a","b","c"]

### Solution using UMPIRE

#### Test cases

    words =   [qnr, anr, nmr] 
    pattern = xnr 
    output = [ qnr, anr, nmr ]

    words = [] -> X
    pattern = pq

    words = [p, f, b] -> X
    pattern = ""

    words =   [ab, dg, pn] -> X
    pattern = abc 

    words = [ASD, 990] -> X 

    patter -> 889 -> X

    words = [abc, pqr] 
    patter = rrr
    output = [ ]

    words = ["abcde","meeme"]
    pattern = "abbab"


#### Match and Plan

    abbab  
        a:0,3
        b:1,2,4

    meeme
        m:0,3
        e:1,2,4


```sh
helper(string):
    map = {}
    res = ""
    iterate string: i
        if string[i] in map:
            map[string]: ..i
        else
            map[string]:i
    
    iterate string: s
        res += map[s]
    return res
    
main()
    result=[]
    pattern_encoded = helper(pattern)
    iterate words: word
        word_pattern = helper(word)
        if word_pattern == pattern_encoded:
            result: add - word
    return result
```

#### Implement

```sh
class Solution:
    def helper(self, string):
        mapping = dict()
        encoded_pattern = ""
        for i in range(len(string)):
            if string[i] in mapping:
                mapping[string[i]].append(i)
            else:
                mapping[string[i]] = [i]
        for s in string:
            for i in mapping[s]:
                encoded_pattern += str(i)
        return encoded_pattern
        
    def findAndReplacePattern(self, words: List[str], pattern: str) -> List[str]:
        result = list()
        pattern_encoded = self.helper(pattern)
        for word in words:
            word_encoded = self.helper(word)
            if len(word) == len(pattern) and word_encoded == pattern_encoded:
                result.append(word)
        return result
```

#### Review and Evaluate

Complexity :
    Let N = length of words and  K = length of each word in words
- Time complexity:
    - O(N*K) 
- Space complexity:
    - O(N*K)