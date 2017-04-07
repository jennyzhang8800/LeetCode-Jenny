**题目**
>英文：Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.



>中文：给定整数数组，判断是否包含重复元素,有重复则返回true,没有重复则返回false.



**leetcode 链接**

https://leetcode.com/problems/contains-duplicate/#/description

**我的思路**


利用set()函数，得到数组中去掉重复之后的数组。判断原数组的大小与去重复之后的数组的大小。如果```len(set(nums))<len(nums)```则说明nums有重复（因为去重之后的数组长度比原数组小）


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


