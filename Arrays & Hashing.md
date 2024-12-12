To enhance navigation within the file, I suggest including a Table of Contents (ToC) section at the start. This provides a clear structure for readers and allows for easy access to each section. Here's the modified content with the Table of Contents added and slight adjustments for better flow:

---

# Mastering Arrays & Hashing: A Comprehensive Guide with Python Solutions

Arrays and hashing are fundamental concepts in data structures and algorithms. Mastering these topics can significantly improve problem-solving skills, especially in coding interviews.

---

## Table of Contents

1. [Introduction to Arrays & Hashing](#introduction-to-arrays--hashing)
2. [Understanding Arrays & Hashing](#understanding-arrays--hashing)
   - [Arrays](#arrays)
   - [Hashing](#hashing)
3. [Key Concepts in Arrays & Hashing](#key-concepts-in-arrays--hashing)
4. [Common Patterns in Arrays & Hashing](#common-patterns-in-arrays--hashing)
5. [Problem-Solving Using Arrays & Hashing: NeetCode Solutions](#problem-solving-using-arrays--hashing-neetcode-solutions)
   - [217. Contains Duplicate](#217-contains-duplicate)
   - [242. Valid Anagram](#242-valid-anagram)

6. [Conclusion](#conclusion)

---

## Introduction to Arrays & Hashing

- **Arrays**: Arrays are ordered collections of elements, all of the same type, stored at contiguous memory locations. Accessing elements by their index is very fast, making arrays useful for quick lookups, but they have fixed sizes in many programming languages.
  
- **Hashing**: Hashing is a technique used to map data to a fixed-size value (called a hash code). Hashing enables fast retrieval of data from hash tables or sets by converting a key into a unique hash value, which helps in quickly locating an item without scanning all items.

---

## Understanding Arrays & Hashing

### Arrays

- **Definition**: An array is a collection of elements, all of the same data type, stored in contiguous memory locations.
  
- **Operations**:
  - **Access**: Accessing an element using its index is \(O(1)\).
  - **Insertion/Deletion**: Inserting or deleting elements can be inefficient because all subsequent elements may need to be shifted.
  - **Traversal**: Iterating through an array takes \(O(n)\).

**Key Operations**:
1. **Accessing elements** by index: `arr[i]`
2. **Traversing** an array: `for num in arr: print(num)`
3. **Inserting/Deleting** elements: Operations may require shifting other elements.

---

### Hashing

- **Definition**: Hashing is the process of converting input into a fixed-size value. This is done using a hash function. Hash maps and sets use hashing to enable fast insertion, deletion, and search operations.

- **Operations**:
  - **Insertion**: Insert a key-value pair into the hash table.
  - **Search**: Retrieve a value using its key in constant time.
  - **Deletion**: Remove an element by key in constant time.

**Key Operations**:
1. **Insert**: `hash_map[key] = value`
2. **Search**: `value = hash_map[key]`
3. **Delete**: `del hash_map[key]`

---

## Key Concepts in Arrays & Hashing

1. **Indexing**: 
   - Arrays provide direct access to elements using an index.
   - Hashing maps keys to values, but the key doesn’t always correspond directly to an index.

2. **Hash Functions**: 
   - A hash function takes an input and converts it to a hash code, which is used to determine the location of the element in a hash table.
   
3. **Hash Collisions**: 
   - Collisions occur when two different keys produce the same hash code. Common collision resolution strategies include **chaining** (storing multiple items at the same index) and **open addressing** (finding the next available spot).

4. **Two-Pointer Technique**: 
   - This technique is used to solve problems involving arrays and lists where you need to find pairs or subarrays with specific properties.

---

## Common Patterns in Arrays & Hashing

1. **Counting Elements**: Use a hash map to count occurrences of each element in an array.
2. **Finding Pairs/Triplets**: Hash maps and the two-pointer technique are helpful for finding pairs or triplets that meet certain conditions.
3. **Subarray Sum/Length Problems**: Prefix sum and hash maps can be used to solve problems involving subarrays with a particular sum or length.
4. **Groupings**: Grouping anagrams or items based on certain properties can be done efficiently with hash maps.

---

## Problem-Solving Using Arrays & Hashing: NeetCode Solutions

### 217. Contains Duplicate

**Problem Statement**:  
Given an integer array `nums`, return `true` if any value appears **more than once** in the array, otherwise return `false`.

### Example:
```plaintext
nums = [1, 2, 3, 3]
```

Output:  
```plaintext
true
```

### Solutions:

#### 1. **Brute Force Solution**

The brute force approach involves checking each pair of elements to see if any two elements are the same. This is a simple but inefficient solution.

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        for i in range(len(nums)):
            for j in range(i + 1, len(nums)):
                if nums[i] == nums[j]:
                    return True
        return False
```

**Time Complexity**: \(O(n^2)\), where \(n\) is the number of elements in `nums`.  
**Space Complexity**: \(O(1)\), as no extra space is used.

#### 2. **Sorting Solution**

We can sort the array first. If there are any duplicates, they will be adjacent in the sorted array, and we can check consecutive elements for equality.

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        nums.sort()
        for i in range(1, len(nums)):
            if nums[i] == nums[i - 1]:
                return True
        return False
```

**Time Complexity**: \(O(n \log n)\), due to the sorting step.  
**Space Complexity**: \(O(1)\) or \(O(n)\), depending on the sorting algorithm used.

#### 3. **Hash Set Solution**

This approach uses a hash set to track the elements we've seen while iterating through the list. If an element is already in the set, we know it's a duplicate.

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        seen = set()
        for num in nums:
            if num in seen:
                return True
            seen.add(num)
        return False
```

**Time Complexity**: \(O(n)\), where \(n\) is the number of elements in the array. Each lookup and insertion in a set is \(O(1)\).  
**Space Complexity**: \(O(n)\), as we store up to \(n\) elements in the set.

#### 4. **Hash Set Length Solution**

Another way to check for duplicates is by comparing the length of the set (which removes duplicates) to the original list length. If they are not equal, there are duplicates.

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return len(set(nums)) < len(nums)
```

**Time Complexity**: \(O(n)\), where \(n\) is the number of elements in the array.  
**Space Complexity**: \(O(n)\), because we are storing all unique elements in the set.

---

Sure! Here's the content added to the existing explanation for easier navigation:

---

### 242. Valid Anagram

### Problem Link
[Valid Anagram Problem](https://leetcode.com/problems/valid-anagram/)

### Description
Given two strings `s` and `t`, return `true` if the two strings are anagrams of each other, otherwise return `false`.

An anagram is a string that contains the exact same characters as another string, but the order of the characters can be different.

### Example 1:
**Input**:  
```python
s = "racecar", t = "carrace"
```
**Output**:  
```python
True
```

### Example 2:
**Input**:  
```python
s = "jar", t = "jam"
```
**Output**:  
```python
False
```

### Constraints:
- `s` and `t` consist of lowercase English letters.

### Recommended Time & Space Complexity

---

## Approaches for Solution

### 1. **Sorting**

**Approach**:  
The first approach is to sort both strings `s` and `t` and then compare the sorted versions of the strings. If both strings are anagrams, they will become identical once sorted.

**Solution Code**:
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
            
        return sorted(s) == sorted(t)
```

**Explanation**:  
- We first check if the lengths of `s` and `t` are the same. If not, we can return `False` immediately, as anagrams must have the same length.
- Then we sort both strings and compare them. If they are equal, the strings are anagrams; otherwise, they are not.

**Time & Space Complexity**:
- **Time Complexity**:  
  \( O(n \log n + m \log m) \), where `n` is the length of string `s` and `m` is the length of string `t`. Sorting each string takes \( O(n \log n) \) and \( O(m \log m) \) time respectively.
  
- **Space Complexity**:  
  \( O(1) \) or \( O(n + m) \), depending on the sorting algorithm. Most algorithms like Python's Timsort use \( O(n) \) extra space, but the theoretical space complexity is \( O(1) \) for in-place sorting.

---

### 2. **Hash Table**

**Approach**:  
In this approach, we use two hash tables (dictionaries) to store the frequency of each character in both strings. If both hash tables are identical, then the strings are anagrams.

**Solution Code**:
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        countS, countT = {}, {}

        for i in range(len(s)):
            countS[s[i]] = 1 + countS.get(s[i], 0)
            countT[t[i]] = 1 + countT.get(t[i], 0)
        return countS == countT
```

**Explanation**:  
- We first check if the lengths of `s` and `t` are the same. If not, we return `False`.
- We initialize two empty hash tables `countS` and `countT`. As we iterate through both strings, we update the frequency count of each character in their respective tables.
- Finally, we compare the two hash tables. If they are equal, the strings are anagrams; otherwise, they are not.

**Time & Space Complexity**:
- **Time Complexity**:  
  \( O(n + m) \), where `n` and `m` are the lengths of strings `s` and `t`. We iterate through each string once to populate the hash tables.
  
- **Space Complexity**:  
  \( O(1) \), as the maximum number of different characters is limited to 26 (lowercase English letters). Therefore, the space complexity is constant.

---

### 3. **Hash Table (Optimal)**

**Approach**:  
This approach uses a single hash table to count the character frequencies in both strings. We update the counts in one pass and check if all counts are zero.

**Solution Code**:
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        count = [0] * 26  # 26 English lowercase letters
        for i in range(len(s)):
            count[ord(s[i]) - ord('a')] += 1
            count[ord(t[i]) - ord('a')] -= 1

        for val in count:
            if val != 0:
                return False
        return True
```

**Explanation**:  
- We first check if the lengths of `s` and `t` are the same. If they are not, we return `False`.
- We use a list `count` of size 26 to track the frequency of characters in both strings. For each character in `s`, we increment its count, and for each character in `t`, we decrement its count.
- After processing both strings, if all values in `count` are zero, the strings are anagrams. Otherwise, they are not.

**Time & Space Complexity**:
- **Time Complexity**:  
  \( O(n + m) \), where `n` and `m` are the lengths of strings `s` and `t`. We process each string once.
  
- **Space Complexity**:  
  \( O(1) \), as we are only using a fixed-size array of length 26 for storing character counts.

---

## Conclusion

There are multiple ways to solve the **Valid Anagram** problem. Each approach has different time and space complexities:

- **Sorting**: Simple but less efficient in terms of time complexity due to sorting.
- **Hash Table**: More efficient as it counts frequencies, but requires two hash tables.
- **Optimal Hash Table**: The most efficient approach in terms of space and time, using a single array to count characters.

Understanding these solutions and their complexities will help you pick the best approach based on the constraints and size of the problem.

---

## Conclusion

Arrays and hashing are vital topics in programming that help in solving a wide variety of problems efficiently. By understanding the core concepts, such as how arrays store elements and how hashing maps data, you can optimize your code and solve complex problems quickly. This guide, along with the solutions and time/space complexity analysis, will help you understand how to approach different kinds of problems related to arrays and hashing. By practicing these problems, you'll be able to build a solid foundation for your coding interviews and improve your problem-solving skills.

---
