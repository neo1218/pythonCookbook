PythonCookBook 1: 数据结构与算法
===

### 1.1: 将序列分解为单独的变量

    这一节的核心在于可迭代对象的分解

    a, b, .... n = (1, 2, 3, .... n)

### 1.2: 从任意长度的可迭代对象中分解元素

    对于长度不确定的分解可以采用"*表达式", 类似于正则表达式中的通配符

### 1.3: 保存最后N个元素

    这一节关键在于一个search函数，以及双端队列的使用

    from collections import deque
    """
    deque 的基本用法即特性:
    >> from collections import deque
    >> # 定长序列
    >> q = deque(maxlen=3)
    >> q.append(1)
    >> q.append(2)
    >> q.append(3)
    >> q
    [1, 2, 3]
    >> q.append(4)
    [2, 3, 4]
    >> # 不定长双端队列
    >> q = deque()
    >> q.append(2)
    >> q.appendleft(1)
    >> q
    [1, 2]
    >> q.popleft()
    1
    >> q
    [2]
    """

    def search(lines, pattern, history=5):
        """在lines查找pettern, 搜索历史为5条"""
        previous_lines = deque(maxlen=history)
        for line in lines:
            if pattern in line:
                yield line, previous_lines
            previous_lines.append(line)

    当编写搜索某项纪录的代码时，通常会用到含有yield关键字的生成器函数,这将处理搜索过程的代码和
    使用搜索结果的代码成功解耦开来。


### 1.4: 找到最大或最小的N个元素

