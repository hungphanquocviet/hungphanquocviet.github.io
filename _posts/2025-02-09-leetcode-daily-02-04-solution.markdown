---
layout: post
title:  "LeetCode daily Feb 4"
date:   2025-02-09 00:01:32 -0700
categories: leetcode solution
---



[Problem Link](https://leetcode.com/problems/check-if-one-string-swap-can-make-strings-equal/description/?envType=daily-question&envId=2025-02-05)

You are given two strings `s1` and `s2` of equal length. A **string swap** is an operation where you choose two indices in a string (not necessarily different) and swap the characters at these indices.

Return `true` _if it is possible to make both strings equal by performing **at most one string swap** on **exactly one** of the strings._ Otherwise, return `false`.

## Intuition and Approach

We are given 2 strings `s1` and `s2`, of same length. Our goal is to determine whether we can make them equal by performing **at most one swap** between two characters in **exactly one** of the strings.

For this to be possible, the following conditions must be met:
1. **At most 2 differences** -- If there are more than 2 indices where `s1[i] != s2[i]`, then swapping one time is not enough
2. **Matching characters for Swap** -- If there are exactly 2 different positions, swapping the corresponding characters in one of the strings must result in equality.

From the observations, we can construct the following approach:
- Iterate through both strings and keep track the indices where `s1[i] != s2[i]`.
- If there are more than 2 mismatches, return `False`, since one swap is not enough.
- Else check whether swapping would result in equality


## Code

Here is the implementation in Python:

{% highlight python %}
class Solution:
    def areAlmostEqual(self, s1: str, s2: str) -> bool:
        not_same = 0
        l1 = []
        l2 = []

        for i in range(len(s1)):
            if s1[i] != s2[i]:
                not_same += 1
                l1.append(s1[i])
                l2.append(s2[i])

        if not_same > 2 or l1[::-1] != l2:
            return False
        return True
{% endhighlight %}
