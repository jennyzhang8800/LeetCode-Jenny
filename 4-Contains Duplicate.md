**题目**
>英文：Given an index k, return the kth row of the Pascal's triangle.

For example, given k = 3,
Return [1,3,3,1].

Note:
Could you optimize your algorithm to use only O(k) extra space?

>中文：给定K，返回第K行的杨辉三角

优化算法只使用O(k)的空间

**leetcode 链接**

https://leetcode.com/problems/contains-duplicate/#/description

**我的思路**

```
利用set()函数，得到数组中去掉重复之后的数组。判断原数组的大小与去重复之后的数组的大小。如果len(set(nums))<len(nums)则说明nums有重复（因为去重之后的数组长度比原数组小）
```

**我的代码**

python

```
class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        return len(set(nums))<len(nums)
        
            
```

**结果**

AC


