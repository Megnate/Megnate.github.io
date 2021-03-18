---
title: python
date: 2021-03-18 16:04:56
tags: 技术
---

**PYTHON**

<!--more-->

Java面试题：https://github.com/JavaInterviewHub/JavaInterview
前端面试题：https://github.com/WebInterviewHub/WebInterview
Python面试题：https://github.com/PythonInterviewHub/PythonInterview

### 迭代时删除列表元素

在迭代时删除列表（list）中的元素时，会使元素的下标（index）发生错位，会造成两种错误

- 使用`list.remove(3)`来删除时，不会提示错误，因为`remove`在找不到对应的数值时会删除**最后一项**，所以可能会出现并没有删除干净的情况
- 使用`del list[3]`来删除时，会提示错误，下标越界：`list index out of range`

存在五种办法解决，但是一般都只使用第一种和最后一种

- 使用`filter`过滤返回新的`list`

  ```python
  list1 = [1,2,1,3]
  
  list1 = filter(lambda x: x != 0, list1)
  ```

  这一种只能删除**指定元素**

- 列表解析

  ```python
  list1 = [x for x in list1 if x != 0]
  ```

  这一种情况，可以在if语句处加一判断，`x`只会保存`x != 0`的元素，这一种写法可以应用于很多的地方

  ```python
  for i in (c for c in coinList if c <= money)
  ```

- 遍历拷贝的`list`，操作原始的`list`

- 用while循环来判断

  ```python
  while o in list1:
      list1.remove(0)
  ```

- 倒序循环遍历

  ```python
  for item in range(len(list1) - 1, -1, -1):
      if list1[item] == 0:
          del list1[item]
  ```

  这一种是==最常用==的，但是可读性较差，所以有时也会使用第一种

实例：

```python
# 获取去除列表中相同的元素之后列表有多少位
def remove(nums:List[int]) -> int:
    newnums = [0]*len(nums)
    for i in range(len(nums) - 1, -1, -1):
        if nums[i] not in newnums:
            newnums[i] = nums[i]
            continue
        else:
            del nums[i]
    return len(nums)
func = remove([1,1,2,1,3,5,3,4])
print(func)
```

