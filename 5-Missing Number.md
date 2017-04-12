**题目**
>英文：Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.

For example,
Given nums = [0, 1, 3] return 2.

Note:
Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?


>中文：给定整数数组，包含从0到n的不同的数字，找到数组中缺少的那个数字。注意：算法应该是线性的时间复杂度，常数的空间复杂度。



**leetcode 链接**

https://leetcode.com/problems/missing-number/#/description

**我的思路**


先给数组nums排序，然后遍历不缺数字的数组，对比nums中是否有对应的数字，如果没有就输出该数字。
需要注意的是，如果nums不缺数字，会输出的是n+1

**我的代码**

python

```
class Solution(object):
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        for item in range(max(nums)+1):
            if item not in nums:
                return item
        return max(nums)+1
            
```

**结果**
TLE

**参考思路**
```
当数组缺少一个数字时：
因为只会缺少一个数字，因此可以用不缺少的数组之和，减去缺少一个数字的数组之和，就可以得到缺少的这个数字。
由于0加到n是等差数列求和：n*n+1/2 .而n刚好是len(nums)。所以结果是sum(n*n+1/2)-sum(nums)
当数组不缺数字时：
由于数组是从0到n的，当不缺少数字的时间输出的是n+1。也就是sum([0,...n,n+1])-sum(nums)，也适用上面的公式。
```
**参考代码**
```
class Solution(object):
    def missingNumber(self, nums):
        n=len(nums)
        return n*n+1/2-sum(nums)

```
