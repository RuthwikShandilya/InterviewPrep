(Sliding Window) Given a list of integers, find the longest contiguous subarray whose sum is less than a given target. Optimize your solution.
(Heap/Sorting) Given a list of numbers, return the K most frequent elements.
from collections import Counter

list_num=[3,1,1,1,1,1,1,1, 2,7,7,7,7,7,77, 4, 2, 1]
k=2
char_count=Counter(list_num)

print(char_count)

sorted_itms=sorted(char_count.items(),key=lambda x:x[1],reverse=True)

for num in sorted_itms[:k]:
    print(num[0])
    
(Two Pointers) Given a sorted list, write a function to find a pair of numbers that sum up to a target. Solve it in O(n) time.
list_num=[1,3,5,6,7,8]

k=15

def findPairSum(list_num,k):
    left=0
    right=len(list_num)-1
    while left<right:
        if list_num[left] +list_num[right] < k:
            left+=1
        if list_num[left] +list_num[right] > k:
            right-=1
        if list_num[left] +list_num[right] == k:
            return  list_num[left],list_num[right]
        
print(findPairSum(list_num,k))
(Sorting & Custom Comparator) Implement a function that sorts a list of numbers in such a way that they form the largest possible concatenated number (e.g., [3, 30, 34, 5, 9] → "9534330").
char_num=[3, 30, 34, 5, 9] 

final_Str="9534330"


def sortStringToList(str):
    return sorted(str,key=lambda x:x,reverse=True)
    
final_list=[]
for ele in char_num:
    final_list+=sortStringToList(str(ele))
    
print(''.join(sorted(final_list,key=lambda x:x,reverse=True)))

(In-place Modification) Rotate a list to the right by k places without using extra space.

(Merging & Deduplication) You have two sorted lists of numbers. Merge them into a single sorted list without duplicates, using O(1) extra space.


##(Palindrome & Expansion) Given a string, find the longest palindromic substring. Optimize beyond brute force.

str_val="abccbal"
i=0

def expandAroundCenter(s,left,right):
    while left>=0 and right<=len(s)-1 and s[left]==s[right]:
        print(f"left:{left} right:{right}")
        left-=1
        right+=1
    return s[left+1:right]


def longestPalindrome(s):
    longest=""
    for i in range(len(s)):
        odd_palindrome=expandAroundCenter(s,i,i)
        even_palindrome=expandAroundCenter(s,i,i+1)
        longest=max(longest,odd_palindrome,even_palindrome,key=len)
    return longest
        
print(longestPalindrome(str_val))


