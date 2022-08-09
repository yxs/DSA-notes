# 回溯

[English](./Backtracking.md)

## 概念

回溯分步试探每种可能性，如果当前不是目标，则退回上一步尝试其他可能，因为大多时候每一步的处理是一样的，所以用递归来解决，一个递归算法一定要有出口，回溯作用到树时就是类似 DFS，几乎所有可以用回溯解决的问题都可以表示为树。

典型问题有

1. 排列、组合（子集、幂集、字符全排列）。 在传值时，对于排列问题，是要删掉单个用过的元素；组合问题，是删掉前面所有的元素
2. 数组、字符串，给定一个特定的规则，尝试搜索迭代找到某个解
3. 二维数组下的 DFS

## 模版 & 基本操作

```python
res = []    # 定义全局变量保存最终结果
state = []  # 定义状态变量保存当前状态，状态变量（state）就是最后结果（result）要保存的值
p, q, r     # 定义条件变量（一般条件变量就是题目直接给的参数），条件变量就是决定搜索是否完毕或者合法的值
def backtrack(状态，条件1，条件2，...):
    if   # 不满足合法条件（可以说是剪枝），搜索失败并返回上一次状态
        return
    elif # 状态满足最终要求，搜索成功并保存结果
        res.append(state)
        return 
    # 主要递归过程，一般是带有 循环体 或者 条件体，传递当前状态给下一次递归进行搜索。选择列表
    for / if  # 满足执行条件
        do    # 做选择
        backtrack(状态，条件1，条件2，...)
        undo  # 撤销选择
backtrack(状态，条件1，条件2，...)
return res
```

- 示例1，[22. 括号生成](https://leetcode-cn.com/problems/generate-parentheses)，给一个数字 n，生成 n 对括号的所有匹配

一个树形结构，从根节点出发，用栈来管理路径上的括号，左括号数量 < 右括号的时候，剪枝

通过 debug 可以观察到

```python
def generateParenthesis(self, n: int) -> List[str]:
    ans = []
    def backtrack(S, left, right):
        # 结束条件，括弧全部用完了
        if len(S) == 2 * n:
            ans.append("".join(S))
            return
        # 左括号数量不大于 n
        if left < n:
            S.append("(") # 做选择
            backtrack(S, left + 1, right)
            S.pop() # 撤销选择
        # 右括号数量小于左括号的数量
        if right < left:
            S.append(")")
            backtrack(S, left, right + 1)
            S.pop()
        # 剪枝
        # if right < left:
        #     return
    backtrack([], 0, 0)
    return ans
```

- 示例2，[46. 全排列](https://leetcode-cn.com/problems/permutations)

## 参考

- [DFS 、动态规划、回溯法、递归之间的关系是什么？ - Jerron的回答 - 知乎](https://www.zhihu.com/question/266403334/answer/698464437)
- [回溯法套路模板 刷通leetcode - Tachibana Kanade的文章](https://zhuanlan.zhihu.com/p/112926891)
- [LeetCode--回溯法心得 - James Ken的文章](https://zhuanlan.zhihu.com/p/51882471)
- [回溯算法入门级详解 + 练习（持续更新）- liweiw](https://leetcode-cn.com/problems/permutations/solution/hui-su-suan-fa-python-dai-ma-java-dai-ma-by-liweiw/)
- [22 括号生成题解](https://leetcode-cn.com/problems/generate-parentheses/solution/gua-hao-sheng-cheng-by-leetcode-solution/)
- [回溯算法详解 - labuladong](https://github.com/labuladong/fucking-algorithm/blob/master/%E7%AE%97%E6%B3%95%E6%80%9D%E7%BB%B4%E7%B3%BB%E5%88%97/%E5%9B%9E%E6%BA%AF%E7%AE%97%E6%B3%95%E8%AF%A6%E8%A7%A3%E4%BF%AE%E8%AE%A2%E7%89%88.md)