**题目**
>英文：Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

Here are few examples.

[1,3,5,6], 5 → 2

[1,3,5,6], 2 → 1

[1,3,5,6], 7 → 4

[1,3,5,6], 0 → 0

>中文：给一个数组和待查找的元素。 要是数组中存在该元素, 则找到它的下标, 否则找到它应该插入的位置



**leetcode 链接**

https://leetcode.com/problems/search-insert-position/#/description

**我的思路**

```
先判断元素是否存在于列表中（target in nums），如果存在则输出下标。

否则：
   如果target比最后一个元素大，则输出列表长度（即为插入位置）
   遍历nums，当target比nums中某个元素小时，该元素所在位置即为target应该插入的位置
```

**我的代码**

python

```

class Solution(object):
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        if(target in nums):
            return nums.index(target)
        else:
            if(target >= nums[-1]):
                return len(nums)
            else:
                for item in nums:
                    if target<= item:
                        return nums.index(item)
#if __name__ =='__main__':
#    nums=[1,3,5]
#    k = 4
#    s=Solution()
#    print s.searchInsert(nums,k)
            

    
```

**结果**

AC

**参考代码**


参考一：
```
class Solution(object):
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """       
        return len([x for x in nums if x<target])
                
```

思路是：遍历一遍nums，找出所有比target小的数组成列表。输出列表长度即为target要插入的位置。找到target时也符合这个规律。

时间复杂度为O(n)


参考二：


```
class Solution(object):
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        return bisect.bisect_left(nums, target)
                
```

思路：二分查找，bisect.bisect_left(nums, target)的作用是返回target查入nums中的位置。查找时间复杂度为O(logn)

### 附：python bisect模块解析

bisect的结构：

```
>>>import bisect
>>>dir(bisect)
['__builtins__', '__doc__', '__file__', '__name__', '__package__', 'bisect', 'bisect_left', 'bisect_right', 'insort', 'insort_left', 'insort_right']
```

使用这个模块的函数前先确保操作的列表是已排序的。

**bisect函数**：查找并返回数据将会插入的位置（不会真的把数插入）

```
>>>data=[1,3,5,6,7]
>>>bisect.bisect(data,2)
1
>>>data
[1,3,5,6,7]
```

**bisect_left函数：**查找并返回数据将会插入的位置，如果有重复，则插入在重复数的左边。（不会真的把数插入）

**bisect_right函数：**查找并返回数据将会插入的位置，如果有重复，则插入在重复数的右边。（不会真的把数插入）
```
>>>data=[1,3,5,6,7]
>>>bisect.bisect_left(data,3)
1
>>>bisect.bisect_right(data,3)
2
>>>data
[1,3,5,6,7]

```

**insort函数** 把数插入列表中，插入结果不会影响原有排序

```
>>>data=[1,3,5,6,7]
>>>bisect.insort(data,2)
>>>data
[1,2,3,5,6,7]
```

**insort_left函数：**把数插入列表中，如果有重复，则插入在重复数的左边。

**insort_right函数：**把数插入列表中，如果有重复，则插入在重复数的右边。


单从结果看，是一样的，但实际插入的位置不同
 ```
>>>data=[1,3,5,6,7]
>>>bisect.insort_left(data,3)
>>>data
[1,3,3,5,6,7]
 
>>>data1=[1,3,5,6,7]
>>>bisect.insort_left(data1,3)
>>>data1
[1,3,3,5,6,7]

```
