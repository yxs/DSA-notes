# 堆 (优先队列)

definition

complete binary tree

https://oi-wiki.org/ds/heap/


https://docs.python.org/3/library/heapq.html, python is min heap, heap[0] is the smallest item.

So in the topK problem, the value needs to take the opposite number.


解法

构造好待堆化的 list，对于 `Counter`，用 tuple 来存储 kv pair

比如 最小堆 `min_heap = [(val, key) for key, val in count.items()]`

最大堆取相反数即可 `max_heap = [(-val, key) for key, val in count.items()]`

这里还用了 tuple 并且反转kv，这样根据v排序，最后反馈结果时也可以直接取到k

`dict.items()` returns a list of dict's (key, value) tuple pairs


堆化 `heapq.heapify(heap)`