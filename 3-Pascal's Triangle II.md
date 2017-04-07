**题目**
>英文：Given an index k, return the kth row of the Pascal's triangle.

For example, given k = 3,
Return [1,3,3,1].

Note:
Could you optimize your algorithm to use only O(k) extra space?

>中文：给定K，返回第K行的杨辉三角

优化算法只使用O(k)的空间

**leetcode 链接**

https://leetcode.com/problems/pascals-triangle-ii/#/description

**我的思路**

```
杨辉三角每一行由上一行得来。即第n+1行的第i个数等于第n行的第i-1个数和第i个数之和，这也是组合数的性质之一。即 C(n+1,i)=C(n,i)+C(n,i-1)
计算下一行时需要在当前行最后补上0，由当前行得出下一行。只输出第k行即可。

     [1] ->       [1,0]
    [1,1] ->     [1,1,0]
   [1,2,1] ->   [1,2,1,0]
  [1,3,3,1] -> [1,3,3,1,0]
```

**我的代码**

python

```

class Solution(object):
    def getRow(self, rowIndex):
        """
        :type rowIndex: int
        :rtype: List[int]
        """

        L=[1]
        for j in range(rowIndex):
            L.append(0)
            L=[L[i-1]+L[i] for i in range(len(L))]
        return L
        
            
```

**结果**

AC


