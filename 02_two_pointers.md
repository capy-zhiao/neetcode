# 👣 双指针（Two Pointers）

> [⬅️ 返回首页](./README.md) ｜ 跟随 [NeetCode Roadmap](https://neetcode.io/roadmap)

## 📋 题目清单

| # | 题目 | 难度 |
| --- | --- | --- |
| 125 | [Valid Palindrome](#125-valid-palindrome) | 🟢 Easy |
| 167 | [Two Sum II - Input Array Is Sorted](#167-two-sum-ii---input-array-is-sorted) | 🟡 Medium |
| 15 | [3Sum](#15-3sum) | 🟡 Medium |
| 11 | [Container With Most Water](#11-container-with-most-water) | 🟡 Medium |
| 42 | [Trapping Rain Water](#42-trapping-rain-water) | 🔴 Hard |

---

## 125. Valid Palindrome

**链接：** https://neetcode.io/problems/is-palindrome/question?list=neetcode150

**思路：**

```
need to lower every character and also filter no-alnum
```

**代码：**

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        left = 0
        right = len(s)-1
        while left <= right:
            while left < right and not s[left].isalnum():
                left += 1
            while left < right and not s[right].isalnum():
                right -= 1

            if s[left].lower() == s[right].lower():
                left += 1
                right -= 1

            else:
                return False

        return True
```



---

## 167. Two Sum II - Input Array Is Sorted

**链接：** https://neetcode.io/problems/two-integer-sum-ii/question?list=neetcode150

**思路：**

```
easy
```

**代码：**

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        left = 0
        right = len(numbers) - 1
        while left < right:
            if numbers[left] + numbers[right] > target:
                    right -= 1

            elif numbers[left] + numbers[right] == target:
                return [left+1, right+1]

            elif numbers[left] + numbers[right] < target:
                left += 1
```



---

## 15. 3Sum

**链接：** https://neetcode.io/problems/three-integer-sum/question?list=neetcode150

**思路：**

```
except the duplicate number
```

**代码：**

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nums.sort()
        result = []
        print(nums)
        for i in range(len(nums)-2):
            left = i+1
            right = len(nums)-1
            target = -nums[i]

            if i >= 1 and nums[i-1] == nums[i]:
                continue
                
            while left < right:

                # print(f"i:{i} nums[i]:{nums[i]} target: {target} nums[left]: {nums[left]} nums[right]: {nums[right]}")
                if nums[left] + nums[right] == target:
                    result.append([nums[i], nums[left], nums[right]])
                    left += 1
                    right -= 1
                    while left < right and nums[left] == nums[left-1]:
                        left += 1
                    while left < right and nums[right] == nums[right+1]:
                        right -= 1

                elif nums[left] + nums[right] > target:
                    right -= 1
                
                elif nums[left] + nums[right] < target:
                    left += 1

            
        return result
```



---

## 11. Container With Most Water

**链接：** https://neetcode.io/problems/max-water-container/question?list=neetcode150

**思路：**

```
hints said everything
```

**代码：**

```python
class Solution:
    def maxArea(self, heights: List[int]) -> int:
        left = 0
        right = len(heights) - 1

        max_result = 0

        while left < right:
            result = (right - left) * min(heights[left], heights[right])
            # print(f"left:{left} right:{right} heights[left]:{heights[left]} heights[right]:{heights[right]} result:{result}")

            max_result = max(result, max_result)

            if left < right and heights[left] <= heights[right]:
                left += 1

            elif left < right and heights[left] > heights[right]:
                right -= 1

            # elif left < right and heights[left] == heights[right]:
            #     left += 1
            #     right -= 1

        return max_result
```



---

## 42. Trapping Rain Water

**链接：** https://neetcode.io/problems/trapping-rain-water/question?list=neetcode150

**思路：**

```
hard不想做
```

**代码：**

```python
# 待补充
```



---

## Other

有一组成绩,将及格的往前面排,不及格的往后面排,不能改变相对位置

**思路：**

```
cant put score which under 60 back, just put score which above 60 forward
```

**代码：**

```python
class Solution:
    def partitionScores(self, scores: List[int]) -> List[int]:
        flag = 0
        for i in range(len(scores)):
            if scores[i] >= 60:
                tmp = scores[i]
                for j in range(i, flag, -1):
                    scores[j] = scores[j - 1]
                scores[flag] = tmp
                flag += 1

        return scores
```

