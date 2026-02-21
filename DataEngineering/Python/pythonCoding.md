# Advanced Python Interview Questions

## Python Decorators 





This document contains 50 advanced Python interview questions covering **strings, lists, and dictionaries**. Mastering these will help you confidently tackle any Python coding interview.

---

## **📌 Advanced String Questions (15)**

1. Given a string, find the longest substring without repeating characters.  
```python
# #Using pointers 
# str="strhellohi"
# list_str=list(str)
# i=0
# longest_sub_string=""
# while i <len(list(str)):
#     new_str_list=[]
#     j=i
#     while j < len(list_str): 
#         if(list_str[j] in new_str_list):
#             break
#         new_str_list.append(list_str[j])
#         j+=1

#     if len(new_str_list) > len(longest_sub_string):
#         longest_sub_string=''.join(new_str_list)
#     i+=1
# print(longest_sub_string)


#Using set 

str="strhellohi"

char_set=set()
i=0
j=0
max_str=""


while j < len(str):
    print(f"i is {str[i]}")
    if str[j] not in char_set:
        char_set.add(str[j])
        j+=1
        
        if j-i > len(max_str):
            print(f"i is {i} j is {j}")
            max_str=str[i:j]
            print(max_str)
    
    else:
        print(char_set)
        char_set.remove(str[i])
        i+=1
print(max_str)

```
2. Implement a function to check if two strings are anagrams of each other.  
```python
from collections import Counter

str="hello"
str1="listen"
str2="silent"
def areAnagrams(str1,str2):
    if(sorted(str1)==sorted(str2)):
        return True
    else:
        return False
print(areAnagrams(str,str2))

def areAnagrams2(str1,str2):
    if(Counter(str2)==Counter(str1)):
        return True
    else:
        return False
print(areAnagrams2(str,str2))
```
3. Find all possible palindromic substrings in a given string.  
```python

str="racecar"

def isPalindrome(str):
    if(str == str[::-1]):
        return str
    else:
        None
i=0
j=0
list_palindrome=set()
while i < len(str):
    j=i+1
    while j < len(str)+1:
        list_palindrome.add(isPalindrome(str[i:j]))
        j+=1
    i+=1
print(list_palindrome)
```
4. Write a function to find the longest palindromic substring in a given string.  
```python
str="racecar"

def isPalindrome(str):
    if(str == str[::-1]):
        return str
    else:
        None
max_palindrome_str=""
i=0
j=0
list_palindrome=set()
while i < len(str):
    j=i+1
    while j < len(str)+1:
        if isPalindrome(str[i:j]):
            if len(max_palindrome_str) < j-i:
                max_palindrome_str=str[i:j]
        j+=1
    i+=1
print(max_palindrome_str)


#Find the longest palindrome substring in a given string.


str_val="sstttts"
max_palindrome_len=0
def isPalindrome(str_val):
    if str_val == str_val[::-1]:
        return True
    else:
        return False
        
i=0
while i <len(str_val):
    j=len(str_val)
    while j> i:
        if isPalindrome(str_val[i:j]):
            max_palindrome_len=j-i
        break
        j=j-1
    if isPalindrome(str_val[i:j]):
        break
    i=i+1
            
    
        
print(max_palindrome_len)

```
5. Implement a function that compresses a string using character counts (e.g., `"aaabbc"` → `"a3b2c1"`).  
```python
from collections import Counter
my_str = "aaabbc"

# Using Counter to count character frequencies
char_count = Counter(my_str)

# Creating the new string with character and their frequencies
str_new = ""
for ele, val in char_count.items():
    str_new += ele + str(val)  # Use the built-in str() function here

print(str_new)
    
```
6. Given two strings, find the minimum window substring from the first that contains all characters of the second.  
```python
from collections import Counter

str1="uhelllo"
str2="hello"

min_str_len=float('inf')


def minWindowSubString(str1,str2):
    i=0
    min_str=""
    while i < len(str1):
        j=i+1
        while j <len(str1)+1:
            if(Counter(str1[i:j]) >= Counter(str2)):
                if(len(str1[i:j]) < min_str_len):
                    min_str=str1[i:j]
            j+=1
        i+=1
    return min_str
            
                

    
print(minWindowSubString(str1,str2))
```
```
8. Find the most frequently occurring word in a paragraph, ignoring common words like "the", "is", etc.  
```python
#Find the most frequently occurring word in a paragraph, ignoring common words like "the", "is", etc

str="""I am preparing for the python course.Python course is the best course and is used for data enalytics and python and Python and the is our out from preparing"""

ignore_words=["the","I","and","is"]
list_para=str.split(" ")
para_word_count={}

for ele in list_para:
    para_word_count[ele]=para_word_count.get(ele,0)+1
    
print(para_word_count)

max_freq=0
max_freq_Word=""

for key in para_word_count.keys():
    if key not in ignore_words:
        if para_word_count.get(key) > max_freq:
            max_freq_Word=key
            max_freq=para_word_count.get(key)
            
        else:
            None
    else:
        None
print(max_freq_Word)
    
```
9. Reverse the order of words in a string without using `split()`.  
```python
str_para="Hi I am python compiler"

result=""
word=""
for i in range(len(str_para)-1,-1,-1):
    if str_para[i] !=" ":
        word=str_para[i]+word
    else:
            result=result+word+" "
            word=""
if word:
    result=result+word
print(result)
```
10. Check if one string is a rotation of another (e.g., `"erbottlewat"` is a rotation of `"waterbottle"`).  
```python
str1="erbottlewat"
str2="waterbottle"

if str2 in (str1 +str1):
    print(True)
else:
    print(False)
    
    
```
11. Remove duplicate characters from a string while preserving the order.  
```python
str="hellooooetg"
sub_str=""

for ele in str:
    if ele not in sub_str:
        sub_str+=ele
print(sub_str)
        
```

13. Given a string containing multiple numbers, extract the largest numerical value.  
```python
import re

str="my current salry for month 29 is 32 and 45 and 1234 5"

numbers=re.findall(r'\d+',str)

print(numbers)
int_numers=[]
for ele in numbers:
    int_numers.append(int(ele))
print(sorted(int_numers)[-1])
```
14. Given a string with nested brackets, check if they are properly balanced (`{[()]}` is valid, `{[(])}` is not).  
```python
bracket_map = {')': '(', '}': '{', ']': '['}
stack=[]
str="{}[]()[["
 
for ele in str:
    if ele in bracket_map.values():
        stack.append(ele)
    if ele in bracket_map.keys():
        if stack.pop() != bracket_map[ele]:
            break
print(stack)
if len(stack) ==0:
    print("valid")
else:
    print("invalid")
     
```
15. Implement a function to group **isomorphic strings** together.
```python
# Your solution here
```

---

input=[1,2,3,10]
smallerst_number=1
for ele in input:
    if ele>smallerst_number:
        break
    smallerst_number+=ele
    
print(smallerst_number)


## **📜 Advanced List Questions (17)**

16. Implement a function that finds the **k-th largest** element in an unsorted list.  
```python
# Your solution here
```
17. Given a list of numbers, find the **subarray** with the maximum sum (Kadane’s Algorithm).  
```python
# Your solution here
```
18. Implement a function to generate all possible **permutations** of a given list.  
```python
# Your solution here
```
19. Given a rotated sorted list, find the **index** where it was rotated.  
```python
# Your solution here
```
20. Implement a function to merge **two sorted lists** without using extra space.  
```python
# Your solution here
```
21. Find the **intersection** and **union** of two lists without using `set()`.  
```python
# Your solution here
```
22. Given a list of numbers, find all **triplets** that sum up to a target value.  
```python
# Your solution here
```
23. Implement a function to **rotate a list** k times to the right.  
```python
# Your solution here
```
24. Given a list of intervals, merge overlapping intervals.  
```python
# Your solution here
```
25. Find the **median** of two sorted lists of different sizes efficiently.  
```python
# Your solution here
```
26. Implement a function to find the **longest consecutive sequence** in an unsorted list.  
```python
# Your solution here
```
27. Implement a function to find **pairs of elements** that sum up to a given target using the **two-pointer technique**.  
```python
# Your solution here
```
28. Given a list of employees with `(name, age, salary)`, sort them by multiple fields (e.g., first by age, then by salary).  
```python
# Your solution here
```
29. Reverse a list in-place without using `.reverse()`.  
```python
# Your solution here
```
30. Given a list of 0s, 1s, and 2s, sort it in-place in **O(n)** time (Dutch National Flag problem).  
```python
# Your solution here
```
31. Implement a function to **shuffle** a list randomly (without using `random.shuffle`).  
```python
# Your solution here
```
32. Implement a **circular queue** using a list.
```python
# Your solution here
```

---

## **📖 Advanced Dictionary Questions (18)**

33. Implement a function to find the **most frequently occurring element** in a dictionary's values.  
```python
# Your solution here
```
34. Implement a **trie (prefix tree)** using a dictionary for efficient prefix searching.  
```python
# Your solution here
```
35. Given a dictionary with employee data, find the **highest paid employee**.  
```python
# Your solution here
```
36. Given a nested dictionary, flatten it into a single dictionary with dot-separated keys.  
```python
# Your solution here
```
37. Implement a function to **merge multiple dictionaries** and sum up values for common keys.  
```python
# Your solution here
```
38. Implement a caching system using **LRU Cache** with a dictionary.  
```python
# Your solution here
```
39. Implement a function that **groups words that are anagrams** using a dictionary.  
```python
# Your solution here
```
40. Write a function to perform **auto-complete suggestions** using a dictionary.  
```python
# Your solution here
```
41. Implement a function to count the frequency of **each character** in a large text file efficiently.  
```python
# Your solution here
```
42. Given a dictionary of words, find the word with the **maximum length**.  
```python
# Your solution here
```

---

## **💡 Next Steps**
These 50 questions cover everything you need to master **strings, lists, and dictionaries** in Python. 💪  
Would you like **solutions** or **hints** for any of these? 🚀
