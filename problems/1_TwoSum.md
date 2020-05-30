## Problem
https://leetcode.com/problems/two-sum

## Key Points
```Array``` ```Hash Table```

## Problem Description
```
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:

Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

## Solution
The easiest solution to come up with is Brute Force. We could write two for-loops to traverse every element, and find the target numbers that meet the requirement. However, the time complexity of this solution is O(N^2), while the space complexity is O(1). Apparently, we need to find a way to optimize this solution since the time complexity is too high. What we could do is to record the numbers we have traversed and the relevant index with a Map. Whenever we meet a new number during traversal, we go back to the Map and check whether the `diff` between this number and the target number appeared before. If it did, the problem has been solved and there's no need to continue.

## Key Points
 - Find the difference instead of the sum
 - Connect every number with its index through the help of Map
 - Less time by more space. Reduce the time complexity from O(N) to O(1)

 ## Code
  - Support Language: Java

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer,Integer> map = new HashMap<>();
        for (int i=0;i<nums.length;i++){
            int complement = target - nums[i];
            if (map.containsKey(complement)){
                return new int[] {map.get(complement),i};
            } 
            map.put(nums[i],i);            
        }
        throw new IllegalArgumentException("No two sum solution");
    }
}
```

***Complexity Anlysis***

- *Time Complexity*: O(N)
- *Space Complexity*：O(N)
