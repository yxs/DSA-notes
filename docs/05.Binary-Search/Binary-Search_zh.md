# 二分查找


> https://en.cppreference.com/w/cpp/container/vector

线性表的实现比较容易，要求最优的性能

- 顺序存储

  顺序表

- 链式存储

  单链表，双链表，循环链表（指针实现）；静态链表（借助数组实现）

vector 可变大小数组，高效静态操作 `get, search`

list 双向链表，高效动态操作 `insert, remove`

---

## 二分查找

- 初始版本

https://dsa.cs.tsinghua.edu.cn/~deng/ds/src_link/vector/vector_search_binary_a.h.htm

- 相对于 a，b 将三个分支改为两个，将 mi 包含到右半分支

https://dsa.cs.tsinghua.edu.cn/~deng/ds/src_link/vector/vector_search_binary_b.h.htm

- 不包含 mi 来判断

```cpp
// 二分查找算法（版本C）：在有序向量的区间[lo, hi)内查找元素e，0 <= lo <= hi <= _size
template <typename T> static Rank binSearch ( T* S, T const& e, Rank lo, Rank hi ) {
    while ( lo < hi ) { //每步迭代仅需做一次比较判断，有两个分支
       Rank mi = ( lo + hi ) >> 1; //以中点为轴点（区间宽度的折半，等效于宽度之数值表示的右移）
       ( e < S[mi] ) ? hi = mi : lo = mi + 1; //经比较后确定深入[lo, mi)或(mi, hi)
    } //成功查找不能提前终止
    return lo - 1; //循环结束时，lo为大于e的元素的最小秩，故lo - 1即不大于e的元素的最大秩
} //有多个命中元素时，总能保证返回秩最大者；查找失败时，能够返回失败的位置
```

https://dsa.cs.tsinghua.edu.cn/~deng/ds/src_link/vector/vector_search_binary_c.h.htm

Fibonacci 查找中，假设元素是有序的

均匀且独立的随机分布，用插值查找猜测轴点 

$mi \approx lo + (hi -lo) \cdot  \frac{e - A[lo]}{A[hi] - A[lo]}$

掌握上述一系列改进的思想与编码

## 起泡排序

起泡排序，通过检查逆序对出现的位置并作标记来优化

- 基本版

https://dsa.cs.tsinghua.edu.cn/~deng/ds/src_link/vector/vector_bubblesort_a.h.htm

- 提前终止版

https://dsa.cs.tsinghua.edu.cn/~deng/ds/src_link/vector/vector_bubblesort_b.h.htm

- 跳跃版

https://dsa.cs.tsinghua.edu.cn/~deng/ds/src_link/vector/vector_bubblesort_c.h.htm

二路归并的精简

 [LightHouse](https://dsa.cs.tsinghua.edu.cn/oj/problem.shtml?id=1144) 两种解法

OJ 上的题需要深刻理解

选择排序 有序在后，前面的无序小于后面的有序

插入排序 input-sensitive 有序在前

注意：线性表中元素的位序从 1 开始，而数组中元素的下标从 0 开始

## 归并排序

## 位图


