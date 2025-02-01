# Advanced Python Interview Questions

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
# Your solution here
```
3. Find all possible palindromic substrings in a given string.  
```python
# Your solution here
```
4. Write a function to find the longest palindromic substring in a given string.  
```python
# Your solution here
```
5. Implement a function that compresses a string using character counts (e.g., `"aaabbc"` → `"a3b2c1"`).  
```python
# Your solution here
```
6. Given two strings, find the minimum window substring from the first that contains all characters of the second.  
```python
# Your solution here
```
7. Implement a function to check if a string follows a given pattern (like regex matching without using regex).  
```python
# Your solution here
```
8. Find the most frequently occurring word in a paragraph, ignoring common words like "the", "is", etc.  
```python
# Your solution here
```
9. Reverse the order of words in a string without using `split()`.  
```python
# Your solution here
```
10. Check if one string is a rotation of another (e.g., `"erbottlewat"` is a rotation of `"waterbottle"`).  
```python
# Your solution here
```
11. Remove duplicate characters from a string while preserving the order.  
```python
# Your solution here
```
12. Implement a function that finds the **edit distance** (Levenshtein distance) between two strings.  
```python
# Your solution here
```
13. Given a string containing multiple numbers, extract the largest numerical value.  
```python
# Your solution here
```
14. Given a string with nested brackets, check if they are properly balanced (`{[()]}` is valid, `{[(])}` is not).  
```python
# Your solution here
```
15. Implement a function to group **isomorphic strings** together.
```python
# Your solution here
```

---

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
