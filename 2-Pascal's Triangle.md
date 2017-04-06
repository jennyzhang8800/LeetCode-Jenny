**题目**
>英文：Given numRows, generate the first numRows of Pascal's triangle.

For example, given numRows = 5,
Return

[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]

>中文：给定numRows,生成杨辉三角的前numRows行

**leetcode 链接**

https://leetcode.com/problems/pascals-triangle/#/description

**我的思路**

```
杨辉三角每一行由上一行得来。即第n+1行的第i个数等于第n行的第i-1个数和第i个数之和，这也是组合数的性质之一。即 C(n+1,i)=C(n,i)+C(n,i-1)
计算下一行时需要在当前行最后补上0，由当前行得出下一行。

     [1] ->       [1,0]
    [1,1] ->     [1,1,0]
   [1,2,1] ->   [1,2,1,0]
  [1,3,3,1] -> [1,3,3,1,0]
```

**我的代码**

python

```

class Solution(object):

      
    def generate(self, numRows):
        """
        :type numRows: int
        :rtype: List[List[int]]
        """
        L=[1]
        PL=[]
        for j in range(numRows):
            #print L
            PL.append(L[::-1])
            L.append(0)
            L = [L[i-1]+L[i] for i in range(len(L))]
        return PL
           
    
```

**结果**

AC

**参考代码**


参考一：
```
class Solution(object):
   def generate(self, numRows):
        res = [[1]]
        for i in range(1, numRows):
            res += [map(lambda x, y: x+y, res[-1] + [0], [0] + res[-1])]
        return res[:numRows]
                
```

思路是：利用map实现。当前行后加0（res[-1] + [0]），与当前行前加0（[0] + res[-1])），相加后得到下一行.

这里返回res[:numRows]而不是返回res的原因是考虑到当numRows=0时，结果应为[]

例如：由[1,3,3,1]得到 [1,4,6,4,1] 的方法为：
```
    1 3 3 1 0 
 +  0 1 3 3 1
 =  1 4 6 4 1
```
