---
toc: false
badges: true
layout: post
description: Reconstruct string
categories: [strings, prefix, palindrome]
title: Can you jump all tiles
date: 2022-01-28
---

## Problem 

You are given a string _s_. Consider the following algorithm applied to this string:

1. Take all the prefixes of the string, and choose the longest palindrome between them.
2. If this chosen prefix contains at least two characters, cut this prefix from _s_ and go back to the first step with the updated string. Otherwise, end the algorithm with the current string _s_ as a result.

Your task is to implement the above algorithm and return its result when applied to string _s_.

## Examples

### Example 1

For _s_ = "aaacodedoc", the output should be solution(_s_) = " ".

- The initial string _s_ = "aaacodedoc" contains only three prefixes which are also palindromes - "a", "aa", "aaa" The longest one between them is "aaa" so we cut if from _s_.
- Now we have string "codedoc". It contains two prefixes which are also palindromes "c" and "codedoc". The longest one between them is "codedoc", so we cut if from the current string and obtain the empty string.
- Finally the algorithm ends on the empty string, so the answer is

### Example 2

For _s_ = "codesignal" the output should be solution(_s_) = "codesignal"

- The initial string _s_ = "'codesignal" contains the only prefix, which is also palindrome This prefix is the longest, but doesn't contain two characters, so the algorithm ends with string "codesignal" as a result.

### Example 3

For _s_ = " ", the output should be solution(_s_) = " ".

## Input/Output

**input  string _s_**
- A string consisting of English lowercase letters.

_Guaranteed constraints:_ \
0 ≤ _s_.length ≤ 1000 

**output string**
- The result of the described algorithm.

