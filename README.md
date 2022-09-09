# 4sum

Given an array nums of n integers, return an array of all the unique quadruplets ```[nums[a], nums[b], nums[c], nums[d]]``` such that:
```
0 <= a, b, c, d < n
a, b, c, and d are distinct.
nums[a] + nums[b] + nums[c] + nums[d] == target
```
You may return the answer in any order.

 
```
Example 1:

Input: nums = [1,0,-1,0,-2,2], target = 0
Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]

Example 2:

Input: nums = [2,2,2,2,2], target = 8
Output: [[2,2,2,2]]
``` 

## Constraints:
```
1 <= nums.length <= 200
-10^9 <= nums[i] <= 10^9
-10^9 <= target <= 10^9
```


# Implementation 1 : Time Limit Exceeded
```java
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        
        List<List<Integer>> response = new ArrayList<>();
        int n = nums.length;
        for(int i = 0; i < n-3; i++) {
            for(int j = i+1; j < n-2; j++) {
                for(int k = j+1; k < n-1; k++) {
                    for(int l = k+1; l < n; l++) {
                        int sum = nums[i] + nums[j] + nums[k] + nums[l];
                        if(sum == target) {
                            List<Integer> result = new ArrayList<>();
                            result.add(nums[i]);
                            result.add(nums[j]);
                            result.add(nums[k]);
                            result.add(nums[l]);
                            if(!isExist(response, result))
                               response.add(result);
                        }
                    }
                }
            }
        }
       return response; 
    }
    
    private boolean isExist(List<List<Integer>> response, List<Integer> result) {
        Set<Integer> numbers = new HashSet<>(result);
        for(List<Integer> list : response) {
           Set<Integer> s1 = new HashSet<>(list);
           if(s1.equals(numbers)) {
               return true;
           } 
        }
        return false;
    }
}
```

