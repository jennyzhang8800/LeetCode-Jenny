**题目**
>英文：Contains Duplicate II

>中文：判断数组内是否有重复元素2


**题目描述**

>英文：Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] and the absolute difference between i and j is at most k.

>中文：给出一个整数数组，判断该数组内是否有两个元素值是相同的，且他们的索引值相差不大于k，是则返回true，否则返回false

**leetcode 链接**

[https://leetcode.com/problems/contains-duplicate-ii/#/description](https://leetcode.com/problems/contains-duplicate-ii/#/description)

**我的代码**

python

```

class Solution(object):
    def containsNearbyDuplicate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: bool
        """
        for item in set(nums):
            if nums.count(item)>1:
                indics=[]
                for index,value in enumerate(nums):
                    if value == item:
                        indics.append(index)
                indics.sort()
                min = indics[1]-indics[0]
                for i in range(len(indics)-1):
                    if indics[i+1] - indics[i] < min:
                        min = indics[i+1] - indics[i]
                if min <= k:
                    return True
        return False
                
#if __name__ =='__main__':
#    nums=[1,3,5,3,1]
#    k = 1
#    s = Solution()
#    print s.containsNearbyDuplicate(nums,k)

    
```

**结果**

TLE(	Time Limit Exceeded)

**参考代码**

```

class Solution(object):
    def containsNearbyDuplicate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: bool
        """
        dic = {}
        for i, v in enumerate(nums):
            if v in dic and i - dic[v] <= k:
                return True
            dic[v] = i
        return False
                
```
