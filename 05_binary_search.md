# 🔍 二分查找（Binary Search）

> [⬅️ 返回首页](./README.md) ｜ 跟随 [NeetCode Roadmap](https://neetcode.io/roadmap)

## 📋 题目清单

| # | 题目 | 难度 |
| --- | --- | --- |
| 704 | [Binary Search](#704-binary-search) | 🟢 Easy |
| 74 | [Search a 2D Matrix](#74-search-a-2d-matrix) | 🟡 Medium |
| 875 | [Koko Eating Bananas](#875-koko-eating-bananas) | 🟡 Medium |
| 153 | [Find Minimum in Rotated Sorted Array](#153-find-minimum-in-rotated-sorted-array) | 🟡 Medium |
| 33 | [Search in Rotated Sorted Array](#33-search-in-rotated-sorted-array) | 🟡 Medium |
| 981 | [Time Based Key-Value Store](#981-time-based-key-value-store) | 🟡 Medium |
| 4 | [Median of Two Sorted Arrays](#4-median-of-two-sorted-arrays) | 🔴 Hard |

二分的关键是想清楚 **边界** 和 **循环条件**，写错一个 `+1 / -1` 就会死循环：

```python
def binary_search(nums, target):
    left, right = 0, len(nums) - 1   # 闭区间 [left, right]
    while left <= right:             # 注意是 <=
        mid = (left + right) // 2    # 防溢出可写 left + (right - left) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```

进阶：不只在数组上二分，还能在「答案范围」上二分（如 875 Koko、以速度为搜索空间）。

---

## 704. Binary Search

**链接：** https://neetcode.io/problems/binary-search/question?list=neetcode150

**思路：**

```
待补充
```

**代码：**

```python
# 待补充
```



---

## 74. Search a 2D Matrix

**链接：** https://neetcode.io/problems/search-2d-matrix/question?list=neetcode150

**思路：**

```
待补充
```

**代码：**

```python
# 待补充
```



---

## 875. Koko Eating Bananas

**链接：** https://neetcode.io/problems/eating-bananas/question?list=neetcode150

**思路：**

```
待补充
```

**代码：**

```python
# 待补充
```



---

## 153. Find Minimum in Rotated Sorted Array

**链接：** https://neetcode.io/problems/find-minimum-in-rotated-sorted-array/question?list=neetcode150

**思路：**

```
待补充
```

**代码：**

```python
# 待补充
```



---

## 33. Search in Rotated Sorted Array

**链接：** https://neetcode.io/problems/search-in-rotated-sorted-array/question?list=neetcode150

**思路：**

```
待补充
```

**代码：**

```python
# 待补充
```



---

## 981. Time Based Key-Value Store

**链接：** https://neetcode.io/problems/time-based-key-value-store/question?list=neetcode150

**思路：**

```
待补充
```

**代码：**

```python
# 待补充
```



---

## 4. Median of Two Sorted Arrays

**链接：** https://neetcode.io/problems/median-of-two-sorted-arrays/question?list=neetcode150

**思路：**

```
待补充
```

**代码：**

```python
# 待补充
```
