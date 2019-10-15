---
layout: post
title: Python栈的实现
categories: Algorithms
description: 用Python实现栈抽象数据类型
keywords: Algorithms,Data Structures,Python
---
记录学习笔记和心得，参考书籍**《Python数据结构与算法分析》**。

### 何谓栈

#### 定义

栈是一种**有序集合**，添加和删除操作总发生在同一端，即“顶端”，另一端称为顶端。

#### 原则

栈遵循**后进先出**原则，即**LIFO(list-in first-out)**，提供了一种基于在集合中的时间来排序的方式。

#### 栗子

考虑栈添加和移除顺序相反的特性（反转特性），浏览网页时，就是把网页存放在一个栈中，点击返回时，反向浏览这些网页。

#### 操作

- Stack()创建一个空栈。不需要参数，返回一个空栈。

- push(item)添加元素到栈的顶端。参数为待添加元素，无返回值。

- pop()移除栈顶端元素。不需要参数，但返回顶端元素，修改栈的内容。

- peek()返回栈顶端元素。不移除，不需要参数，也不更改栈的内容。

- isEmpty()检查栈是否为空。不需要参数，返回布尔值。

- size()返回栈中元素数目。不需要参数，返回一个整数值。

### Python实现栈

使用列表实现栈。

``` python
class Stack():
    def __init__(self):
        self.items = []
        
    def isEmpty(self):
        return self.items == []
    
    def push(self,item):
        self.items.append(item)
        
    def pop(self):
        return self.items.pop()
    
    def peek(self):
        return self.items[len(self.items)-1]
    
    def size(self):
        return len(self.items)
    
```

以上代码将列表尾部当作栈顶，可以利用列表的append和pop方法，复杂度为O(1)。如果将列表头部当作栈顶，复杂度将会变成O(n)。

### 栈的应用

#### 匹配符号

符号*()[]{}*混用时应该保证左右符号匹配，类型一致。以下代码判断含有这三种符号的字符串s格式是否正确。

```python
def parchecker(s):

    '''判断符号串格式是否正确'''
    par = {'(':')','{':'{','[':']'}
    stack = Stack()

    for i in range(len(s)):
        if s[i] in '([{':
            stack.push(s[i])
        else:
            if stack.isEmpty():
                return False
            else:
                if s[i] != par[stack.pop()]:
                    return False
    if stack.isEmpty():
        return True
    else:
        return False
```

#### 进制转换

十进制数转换成任意进制数，每次除以基数，将余数压入栈，地板除结果继续执行上述过程，直到十进制数变为0，余数序列倒序就是转换结果。

```python
def baseConverter(decNumber, base):
    digits = '0123456789ABCDEF'
    
    remstack = Stack()
    
    while decNumber > 0:
        rem = decNumber % base
        remstack.push(rem)
        decNumber = decNumber // base
    newstring = ''
    while not remstack.isEmpty():
        newstring += digits[remstack.pop()]
    return newstring
```

