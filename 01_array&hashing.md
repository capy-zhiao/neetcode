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



---

## 347. Top K Frequent Elements

**链接：** https://neetcode.io/problems/top-k-elements-in-list/question?list=neetcode150

**思路：**

```
also use Counter
```

**代码：**

```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        nums1 = Counter(nums)
        # print(nums1)
        nums1 = nums1.most_common()
        # print(nums1)
        result = []
        for n in nums1[:k]:
            # print(n[0])
            result.append(n[0])

        return result
```



---

## 271. Encode and Decode Strings

**链接：** https://neetcode.io/problems/string-encode-and-decode/question?list=neetcode150

**思路：**

```
我不行了,就这样浑水摸鱼
```

**代码：**

```python
class Solution:

    def encode(self, strs: List[str]) -> str:
        if not strs:
            return "~e"
        tmp = "youcanneverguess"
        return tmp.join(strs)
    def decode(self, s: str) -> List[str]:
        if s == "~e":
            return []
        tmp = "youcanneverguess"
        return s.split(tmp)

```



---

## 238. Product of Array Except Self

**链接：** https://neetcode.io/problems/products-of-array-discluding-self/question?list=neetcode150

**思路：**

```
basic:
iterate the list twice and get the result
Multiply by each number expect the target number.

follow-up:
use a suffix and prefix list to store suffix and prefix of each element.
```

**代码：**

```python
# basic
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        result = []
        for i in range(len(nums)):
            tmp = 1
            for j in range(len(nums)):
                if j == i:
                    continue
                tmp = tmp * nums[j]
            result.append(tmp)

        # print(result)
        return result


# Follow-up: Could you solve it in O(n) time without using the division operation?
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        length = len(nums)
        prefix = [1]*length
        suffix = [1]*length

        for i in range(1, length):
            prefix[i] = prefix[i - 1] * nums[i - 1]

        for i in range(length-2, -1, -1):
            suffix[i] = suffix[i+1] * nums[i+1]

        return [prefix[i] * suffix[i] for i in range(length)]
```

---

## 36. Valid Sudoku

**链接：** https://neetcode.io/problems/valid-sudoku/question?list=neetcode150

**思路：**

```
use hash set to detect, because when we create hash set, it will remove depulicate number.

We can build three kinds of hash set, row, column, 3x3.
```

**代码：**

```python
class Solution:
    def valid_row(self, board: [List[List[str]]]) -> bool:
        for list1 in board:
            list1 = [c for c in list1 if c != '.']
            if len(set(list1)) != len(list1):
                return False
        return True

    def valid_column(self, board: [List[List[str]]]) -> bool:
        for col in range(9):
            list2 = [board[i][col] for i in range(9) if board[i][col] != '.']
            if len(set(list2)) != len(list2):
                return False
        return True

    def threeplusthree(self, board: [List[List[str]]]) -> bool:
        for row in range(0, 9, 3):
            for col in range(0, 9, 3):
                list3 = [board[row+i][col+j] for i in range(3) for j in range(3) if board[row+i][col+j]!='.']
                if len(set(list3)) != len(list3):
                    return False
        return True

    def isValidSudoku(self, board: List[List[str]]) -> bool:

        if not self.valid_row(board): return False
        if not self.valid_column(board): return False
        if not self.threeplusthree(board): return False
        return True
```



---

## 128. Longest Consecutive Sequence

**链接：** https://neetcode.io/problems/longest-consecutive-sequence/question?list=neetcode150

**思路：**

```
Using hash set to get the O(n)
first, accroding to the hint, I store numbers which its (minus 1) value not exist in nums list in start list.
And then, iterate the start list, gradually increment by 1 to check if the number is in the list nums.
if yes, then length add 1, 
Finally, we got the max_length.
```

**代码：**

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        hash_nums = set(nums)
        start = []
        for i in hash_nums:
            if (i-1) not in hash_nums:
                start.append(i)

        max_length = 0
        for num in start:
            i = 1
            while (num+i) in hash_nums:
                i+=1
            max_length = max(i, max_length)

        return max_length

```



---
