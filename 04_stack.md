# 📐 栈（Stack）

> [⬅️ 返回首页](./README.md) ｜ 跟随 [NeetCode Roadmap](https://neetcode.io/roadmap)

## 📋 题目清单

| # | 题目 | 难度 |
| --- | --- | --- |
| 20 | [Valid Parentheses](#20-valid-parentheses) | 🟢 Easy |
| 155 | [Min Stack](#155-min-stack) | 🟡 Medium |
| 150 | [Evaluate Reverse Polish Notation](#150-evaluate-reverse-polish-notation) | 🟡 Medium |
| 22 | [Generate Parentheses](#22-generate-parentheses) | 🟡 Medium |
| 739 | [Daily Temperatures](#739-daily-temperatures) | 🟡 Medium |
| 853 | [Car Fleet](#853-car-fleet) | 🟡 Medium |
| 84 | [Largest Rectangle in Histogram](#84-largest-rectangle-in-histogram) | 🔴 Hard |

栈的核心是「后进先出（LIFO）」，常见两类套路：

- **括号 / 匹配类**：遇到左括号入栈，遇到右括号弹出比对。
- **单调栈（Monotonic Stack）**：维护一个递增或递减的栈，常用来求「下一个更大 / 更小元素」。

```python
def monotonic_stack(nums):
    stack = []  # 通常存下标，方便算距离
    result = [0] * len(nums)
    for i, x in enumerate(nums):
        # 当栈顶不满足单调性时，弹出并结算
        while stack and nums[stack[-1]] < x:
            j = stack.pop()
            result[j] = i - j      # 例如：下一个更大元素的距离
        stack.append(i)
    return result
```

---

## 20. Valid Parentheses

**链接：** https://neetcode.io/problems/validate-parentheses/question?list=neetcode150

**思路：**

```
待补充
```

**代码：**

```python
class Solution:
    def isValid(self, s: str) -> bool:
        if len(s) % 2 == 1: return False

        bracket = {'(':')', '{':'}', '[':']'}
        flag = ['{', '(', '[']
        stack = []

        for i in s:
            if i in flag:
                stack.append(i)

            else:
                if not stack: 
                    return False
                elif i == bracket[stack[-1]]:
                    stack.pop()
                else:
                    return False
        
        if not stack:
            return True

        else:
            return False


```



---

## 155. Min Stack

**链接：** https://neetcode.io/problems/minimum-stack/question?list=neetcode150

**思路：**

```
remenber pop the minstack
```

**代码：**

```python
class MinStack:

    def __init__(self):
        self.stack = []
        self.minStack = []

    def push(self, val: int) -> None:
        self.stack.append(val)
        val = min(val, self.minStack[-1] if self.minStack else val)
        self.minStack.append(val)

    def pop(self) -> None:
        self.stack.pop()
        self.minStack.pop()

    def top(self) -> int:
        return self.stack[-1]

    def getMin(self) -> int:
        return self.minStack[-1]
```



---

## 150. Evaluate Reverse Polish Notation

**链接：** https://neetcode.io/problems/evaluate-reverse-polish-notation/question?list=neetcode150

**思路：**

```
待补充
```

**代码：**

```python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        tmp = deque()

        for token in tokens:
            if token in "+*-/":
                b = tmp.pop()
                print(f"a:{b}")
                a = tmp.pop()
                print(f"b:{a}")

                if token == "+": tmp.append(a+b)
                if token == "*": tmp.append(a*b)
                if token == "-": tmp.append(a-b)
                if token == "/": tmp.append(int(a/b))

            else:
                tmp.append(int(token))

        return int(tmp[0])
```



---

## 739. Daily Temperatures

**链接：** https://neetcode.io/problems/daily-temperatures/question?list=neetcode150

**思路：**

```
in order to build an On solution
we can use a stack to store each element's index
and the result is the minus between them

```

**代码：**

```python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        result = [0]*len(temperatures)
        stack = []

        for i in range(len(temperatures)):
            print(f"------{i}-------")

            if not stack:
                stack.append(i)
                print(f"stack:{stack}")

            elif temperatures[i] <= temperatures[stack[-1]]:
                stack.append(i)
                print(f"stack:{stack}")

            else:
                print(f"i:{i} temperatures[i]:{temperatures[i]}"
                f"stack[-1]:{stack[-1]}temperatures[stack[-1]]:{temperatures[stack[-1]]}")

                while stack and temperatures[i] > temperatures[stack[-1]]:
                    result[stack[-1]] = i-stack[-1]
                    stack.pop()
                    
                    print(f"after pop : {stack}")

                stack.append(i)
                print(f"{stack}")


        return result

```



---

## 853. Car Fleet

**链接：** https://neetcode.io/problems/car-fleet/question?list=neetcode150

**思路：**

```
待补充
```

**代码：**

```python
# 待补充
```



---

## 84. Largest Rectangle in Histogram

**链接：** https://neetcode.io/problems/largest-rectangle-in-histogram/question?list=neetcode150

**思路：**

```
待补充
```

**代码：**

```python
# 待补充
```
