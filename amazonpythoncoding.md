### Merge Sort 
TimeComplexity: O(nlogn)
```
#Write a function to sort an array so it produces only odd number

input_num=[2,3,5,4,9,7,6,1]

def mergeSort(nums):
    if len(nums)>1:
        left_array=nums[:len(nums)//2]
        right_array=nums[len(nums)//2:]
        mergeSort(left_array)
        mergeSort(right_array)
        
        #Merging arrays
        i=0
        j=0
        k=0
        while i<len(left_array) and j<len(right_array):
            print(f"left_array:{left_array}right_array:{right_array},nums:{nums}")
            if left_array[i]<right_array[j]:
                nums[k]=left_array[i]
                i+=1
            else:
                nums[k]=right_array[j]
                j+=1
            k+=1
            
        while i <len(left_array):
            nums[k]=left_array[i]
            i+=1
            k+=1
        
        while j < len(right_array):
            nums[k]=right_array[j]
            j+=1
            k+=1
    return nums
print(mergeSort(input_num))
        
        
```

### target sum pair

```
#Write code to find the sum of any two numbers in a given array that could be equal to x.

input_num=[1,2,3,4,5,6,7,8]
target=9
output_num=[]
input_set=set()
for ele in input_num:
    if target-ele in input_set:
        output_num.append((ele,target-ele))
    else:
        input_set.add(ele)
        
print(output_num)
```

##is perfect square optimized approach 

```
#is perfect Square



def isPerfectSquare(n):
    if n<0:
        return False
    left,right=0,n
    while left<=right:
        mid=(left+right)//2
        square=mid*mid
        print(mid,square,left,right)
        if square == n:
            return True
        elif square<n:
            left=mid+1
        else:
            right=mid-1
    return False
    
print(isPerfectSquare(14))
```

MAx sum array 

```
class Solution:
	def findMaxSubarraySum(self, nums: List[int]) -> int:
		max_sub_array=[]
		max_sum_array=float('-inf')
		for i in range(len(nums)):
			for j in range(i,len(nums)):
				if sum(nums[i:j+1]) > max_sum_array:
					max_sum_array=sum(nums[i:j+1])
					max_sub_array=nums[i:j+1]
		
		return max_sum_array

```
