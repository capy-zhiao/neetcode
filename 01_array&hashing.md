# 📦 数组与哈希（Arrays & Hashing）

> [⬅️ 返回首页](./README.md) ｜ 跟随 [NeetCode Roadmap](https://neetcode.io/roadmap)

## 📋 题目清单

| # | 题目 | 难度 |
| --- | --- | --- |
| 217 | [Contains Duplicate](#217-contains-duplicate) | 🟢 Easy |
| 242 | [Valid Anagram](#242-valid-anagram) | 🟢 Easy |
| 1 | [Two Sum](#1-two-sum) | 🟢 Easy |
| 49 | [Group Anagrams](#49-group-anagrams) | 🟡 Medium |
| 347 | [Top K Frequent Elements](#347-top-k-frequent-elements) | 🟡 Medium |
| 271 | [Encode and Decode Strings](#271-encode-and-decode-strings) | 🟡 Medium |
| 238 | [Product of Array Except Self](#238-product-of-array-except-self) | 🟡 Medium |
| 36 | [Valid Sudoku](#36-valid-sudoku) | 🟡 Medium |
| 128 | [Longest Consecutive Sequence](#128-longest-consecutive-sequence) | 🟡 Medium |

---

## 217. Contains Duplicate

**链接：** https://neetcode.io/problems/duplicate-integer/question?list=neetcode150

**思路：**

```
Use Counter to organize the nums array, because it shows the number of occurrences of each element.
It has a specific method named most_common(), which orders them from highest to lowest, so if the first element's occurrence count is greater than 1, you know it's True.
```

**代码：**

```python
from collections import Counter

class Solution:
    def hasDuplicate(self, nums: List[int]) -> bool:
        if len(nums) == 0:
            return False
        a = Counter(nums)
        results = a.most_common()
        if results[0][1] > 1:
            return True
        else:
            return False
```

**复杂度：** 时间 O() / 空间 O()

---

## 242. Valid Anagram

**链接：** https://neetcode.io/problems/is-anagram/question?list=neetcode150

**思路：**

```
use Counter as well
```

**代码：**

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        s1 = Counter(s)
        print(s1)
        s2 = Counter(t)
        print(s2)
        print(s1 == s2)
        return s1 == s2

```

**复杂度：** 时间 O() / 空间 O()

---

## 1. Two Sum

**链接：** https://neetcode.io/problems/two-integer-sum/question?list=neetcode150

**思路：**

```
brute force
```

**代码：**

```python
        for i in range(len(nums)-1):
            for j in range(i+1, len(nums)):
                result = nums[i]+nums[j]
                if result == target:
                    return [i, j]
```

**复杂度：** 时间 O() / 空间 O()

---

## 49. Group Anagrams

**链接：** https://neetcode.io/problems/anagram-groups/question?list=neetcode150

**思路：**

```
build a box for each string to count their occurrences of each elements.
and then use the box as the key.
the strings with same key will be put in the same box.
```

**代码：**

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        groups = defaultdict(list)

        for s in strs:
            count = [0]*26
            for ch in s:
                count[ord(ch) - ord('a')] += 1
            key = tuple(count)
            # print(key)
            groups[key].append(s)
            # print(count)

        result = []
        for key, values in groups.items():
            result.append(values)
        return result
```

**复杂度：** 时间 O() / 空间 O()

---

## 347. Top K Frequent Elements

**链接：** https://leetcode.com/problems/top-k-frequent-elements/

**思路：**

```

```

**代码：**

```python

```

**复杂度：** 时间 O() / 空间 O()

---

## 271. Encode and Decode Strings

**链接：** https://leetcode.com/problems/encode-and-decode-strings/

**思路：**

```

```

**代码：**

```python

```

**复杂度：** 时间 O() / 空间 O()

---

## 238. Product of Array Except Self

**链接：** https://leetcode.com/problems/product-of-array-except-self/

**思路：**

```

```

**代码：**

```python

```

**复杂度：** 时间 O() / 空间 O()

---

## 36. Valid Sudoku

**链接：** https://leetcode.com/problems/valid-sudoku/

**思路：**

```

```

**代码：**

```python

```

**复杂度：** 时间 O() / 空间 O()

---

## 128. Longest Consecutive Sequence

**链接：** https://leetcode.com/problems/longest-consecutive-sequence/

**思路：**

```

```

**代码：**

```python

```

**复杂度：** 时间 O() / 空间 O()

---
