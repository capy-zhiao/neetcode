# 🪟 滑动窗口（Sliding Window）

> [⬅️ 返回首页](./README.md) ｜ 跟随 [NeetCode Roadmap](https://neetcode.io/roadmap)

## 📋 题目清单

| # | 题目 | 难度 |
| --- | --- | --- |
| 121 | [Best Time to Buy and Sell Stock](#121-best-time-to-buy-and-sell-stock) | 🟢 Easy |
| 3 | [Longest Substring Without Repeating Characters](#3-longest-substring-without-repeating-characters) | 🟡 Medium |
| 424 | [Longest Repeating Character Replacement](#424-longest-repeating-character-replacement) | 🟡 Medium |
| 567 | [Permutation in String](#567-permutation-in-string) | 🟡 Medium |
| 76 | [Minimum Window Substring](#76-minimum-window-substring) | 🔴 Hard |
| 239 | [Sliding Window Maximum](#239-sliding-window-maximum) | 🔴 Hard |

滑动窗口的题型高度模板化：

```python
def sliding_window(s):
    left = 0
    state = ...  # 视情况：一个 sum、一个 Counter、一个 set
    best = 0
    for right in range(len(s)):
        # 1. 把 s[right] 加入窗口
        ...
        # 2. 当窗口"不合法"时，收缩左边界
        while not_valid(state):
            # 把 s[left] 移出窗口
            ...
            left += 1
        # 3. 此刻窗口合法，更新答案
        best = max(best, right - left + 1)
    return best
```

---

## 121. Best Time to Buy and Sell Stock

**链接：** https://neetcode.io/problems/buy-and-sell-crypto/question?list=neetcode150

**思路：**

```
for each value, select the min_value before it, but the first one its On^2, let me think about a faster way:

O(n):
store the min_value into a parameter

```

**代码：**

```python
# On^2
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        max_ = 0
        for i in range(len(prices)):
            if i == 0: continue
            # print(prices[0:i])
            max_ = max(max_, prices[i] - min(prices[0:i]))
            # print(max_)
        return max_

# On
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        max_value = 0
        min_value = float('inf')
        for i in range(len(prices)):
            min_value = min(min_value, prices[i])
            if i == 0: continue
            max_value = max(max_value, prices[i] - min_value)
        return max_value
```



---

## 3. Longest Substring Without Repeating Characters

**链接：** https://neetcode.io/problems/longest-substring-without-duplicates/question?list=neetcode150

**思路：**

```
use the framework to solve this 
```

**代码：**

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        left = 0
        seen = set()
        result = 0

        for right in range(len(s)):
            
            while(s[right] in seen):
                seen.remove(s[left])
                left += 1

            seen.add(s[right])
            result = max(result, right -left +1)

        return result
```



---

## 424. Longest Repeating Character Replacement

**链接：** https://neetcode.io/problems/longest-repeating-substring-with-replacement/question?list=neetcode150

**思路：**

```
the same framework but with a different constraint
```

**代码：**

```python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        c = Counter()              # 字符 -> 出现次数
        left = 0
        result = 0

        for right in range(len(s)):
            # 1. 新字符进窗口：count[s[right]] += 1
            c[s[right]] += 1
            
            # 2. 当窗口不合法时收缩：
            #    while (窗口长度 - max(count.values())) > k:
            #        count[s[left]] -= 1
            #        left += 1
            while((right - left + 1) - max(c.values())) > k:
                c[s[left]] -= 1
                left += 1

            
            # 3. 更新答案：result = max(result, 窗口长度)
            result = max(result, right - left + 1)
        return result
```



---

## 567. Permutation in String

**链接：** https://neetcode.io/problems/permutation-string/question?list=neetcode150

**思路：**

```
I use Counter to do it first
```

**代码：**

```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        if len(s1) > len(s2): return False
        c1 = Counter(s1)

        for i in range(len(s2)):
            if len(s2) - i >= len(s1):
                tmp = Counter(s2[i:(i+len(s1))])
                if tmp == c1:
                    return True
            else:
                return False

        return False
```



---

## 76. Minimum Window Substring

**链接：** https://neetcode.io/problems/minimum-window-with-characters/question?list=neetcode150

**思路：**

```
待补充
```

**代码：**

```python
# 待补充
```



---

## 239. Sliding Window Maximum

**链接：** https://neetcode.io/problems/sliding-window-maximum/question?list=neetcode150

**思路：**

```
待补充
```

**代码：**

```python
# 待补充
```
