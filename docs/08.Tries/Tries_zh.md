# 字典树 (前缀树)

## 概念

208. Implement Trie (Prefix Tree)


## 模版 & 基本操作

use dict

```python
class Trie:
    ################### 比比较通用的模板 ######################
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.child = dict()
        self.isword = False

    def insert(self, word: str) -> None:
        """
        Inserts a word into the trie.
        """
        rt = self  ##########相当于c++的this指针！！！
        for w in word:
            if w not in rt.child:  # 没有，就新建
                rt.child[w] = Trie()
            rt = rt.child[w]  # 往下走
        rt.isword = True  # 标记位

    def search(self, word: str) -> bool:
        """
        Returns if the word is in the trie.
        """
        rt = self  ##########相当于c++的this指针！！！
        for w in word:
            if w not in rt.child:  # 有字母不在这条path上，断了
                return False
            rt = rt.child[w]  # 沿着path往下走
        return rt.isword == True  # 看isword位

    def startsWith(self, prefix: str) -> bool:
        """
        Returns if there is any word in the trie that starts with the given prefix.
        """
        rt = self  ##########相当于c++的this指针！！！
        for w in prefix:
            if w not in rt.child:  # path断了
                return False
            rt = rt.child[w]
        return True  # 无论是否是单词，path没断就ok


# Your Trie object will be instantiated and called as such:
# obj = Trie()
# obj.insert(word)
# param_2 = obj.search(word)
# param_3 = obj.startsWith(prefix)

```

use array

```python
class Trie:
    ################### 比比较通用的模板 ######################
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.child = [None for _ in range(26)]
        self.isword = False

    def insert(self, word: str) -> None:
        """
        Inserts a word into the trie.
        """
        rt = self  ##########相当于c++的this指针！！！
        for w in word:
            ID = ord(w) - ord("a")
            if rt.child[ID] == None:  # 没有，就新建
                rt.child[ID] = Trie()
            rt = rt.child[ID]  # 往下走
        rt.isword = True  # 标记位

    def search(self, word: str) -> bool:
        """
        Returns if the word is in the trie.
        """
        rt = self  ##########相当于c++的this指针！！！
        for w in word:
            ID = ord(w) - ord("a")
            if rt.child[ID] == None:  # 有字母不在这条path上，断了
                return False
            rt = rt.child[ID]  # 沿着path往下走
        return rt.isword == True  # 看isword位

    def startsWith(self, prefix: str) -> bool:
        """
        Returns if there is any word in the trie that starts with the given prefix.
        """
        rt = self  ##########相当于c++的this指针！！！
        for w in prefix:
            ID = ord(w) - ord("a")
            if rt.child[ID] == None:  # path断了
                return False
            rt = rt.child[ID]
        return True  # 无论是否是单词，path没断就ok


# Your Trie object will be instantiated and called as such:
# obj = Trie()
# obj.insert(word)
# param_2 = obj.search(word)
# param_3 = obj.startsWith(prefix)
```

## 参考

[Trie 维基百科](https://zh.wikipedia.org/wiki/Trie)

[Trie Tree 的实现 (适合初学者)](https://leetcode.cn/problems/implement-trie-prefix-tree/solution/trie-tree-de-shi-xian-gua-he-chu-xue-zhe-by-huwt/)

[c++/python3 Trie通用模板 法1：字典hash 法2：数组](https://leetcode.cn/problems/implement-trie-prefix-tree/solution/c-python3-trietong-yong-mo-ban-fa-1zi-di-0fyw/)