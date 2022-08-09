# What is dynamic programming?

Simple Story https://qr.ae/pNdot8, repeating subproblems.

https://www.zhihu.com/question/23995189/answer/613096905, Detailed explanation(Chinese).

[动态规划问题思考方向](https://pic.leetcode.cn/1f95da43d1bdeebdd1213bb804034ddc5f906dc61451cd63f2b5ab5d0eb33b33-「动态规划」问题思考方向.png), Problem solving ideas(Chinese).

all in all.

- Change space for time, use one-dimensional and multi-dimensional arrays to record states

## Concept

post-invalidity 无后效性：如果给定某一阶段的状态，则在这一阶段以后过程的发展不受这阶段以前各段状态的影响。

optimal substructure 最优子结构：大问题的最优解可以由小问题的最优解推出。

能拆分成子问题且符合上述 2 个条件，就可以用 DP 解决问题。

top-down with memoization 带备忘的自顶向下 vs bottom-up method 自底向上法，为什么 DP 通常要倒推？因为 初态（起点）唯一，目标状态（终点）不唯一。  https://www.zhihu.com/question/464263211/answer/1940236681 

## Space optimization

Scrolling array ideas, variables instead of arrays, such as 152. Maximum Product Subarray

Two-dimensional to one-dimensional, one-dimensional to 2 var.

## Problem solving steps

### Why DP?

既然 DP 是通过子问题优化

transition function

Simple Story https://qr.ae/pNdot8, repeating subproblems

https://www.zhihu.com/question/23995189/answer/613096905