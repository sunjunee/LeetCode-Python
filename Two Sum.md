## Two Sum

https://leetcode.com/problems/two-sum/description/

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

#### Example:
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

#### My Solution:
1. Time: O(n^2), Space: O(1)

  使用暴力解法，对数组进行循环。但是会报超过规定时间的错误。所以python进行暴力循环不可取。

```python
class Solution:
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        for i in range(0, len(nums)-1):
          for j in range(i + 1, len(nums)):
            if(nums[i] + nums[j] == target):
              return [i, j]
```

对程序加以优化，我们使用list中的index功能，适当降低查找的时间


```python
class Solution:
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        for i, n in enumerate(nums):
            if((target - n) in nums[i+1:]):
                return [i, nums[i+1:].index(target-n) + i + 1]
```

耗时 936 ms

2. Time: O(n), Space(n)

  建立hash表，方便索引，降低搜索时间。这里我们用字典实现

（1）字典

```python
class Solution:
   def twoSum(self, nums, target):
       """
       :type nums: List[int]
       :type target: int
       :rtype: List[int]
       """
       nums_dict = {};
       for i, n in enumerate(nums):
           if((target - n) in nums_dict.keys()):
               return [nums_dict[target - n], i]
           nums_dict[n] = i      
```

耗时 40 ms


因此，这一题可以看做是，牺牲空间复杂度来换取时间复杂度的案例。
