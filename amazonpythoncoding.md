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
