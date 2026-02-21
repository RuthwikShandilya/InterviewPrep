Maximum Subarray : 

Use Kadane algorithm which use when ever you get a negatie sum we dont need that elements that can add to maximum sum so we dont use them.

main logic is we iterate through elements find the current_sum and update the max_sum to max(current_sum,max_sum)
and if current_sum<0 we move this current_sum to 0 

```
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        max_sum=float('-inf')
        current_sum=0
        for ele in nums:
            current_sum+=ele
            max_sum=max(current_sum,max_sum)
            if current_sum<0:
                current_sum=0
        return max_sum
            
        
```
