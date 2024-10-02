
# Advanced Coding
Advanced coding tests your problem-solving skills through writing algorithms and optimizing solutions.

## Top 5 Topics
1. **Data Structures**
   - Arrays, linked lists, stacks, queues
2. **Algorithms**
   - Sorting, searching algorithms (e.g., Binary Search, Quick Sort)
3. **Dynamic Programming**
   - Solving problems by breaking them into subproblems
4. **Recursion**
   - Writing recursive functions for problems
5. **Object-Oriented Programming**
   - Understanding and applying OOP concepts (encapsulation, inheritance, polymorphism)

Here's a detailed update for the **Advanced Coding** section of the markdown file, including 10 coding questions with answers and brief descriptions of the methods used:


The **Advanced Coding** section tests your problem-solving skills, algorithm efficiency, and coding abilities. Below are 10 essential coding questions, each with a detailed solution approach and the code to implement it.

---

## 1. Reverse a String

### Problem:
Given a string, reverse it.

### Approach:
- Use two-pointer technique or in-built functions to reverse the string.

### Solution:
```python
def reverse_string(s):
    return s[::-1]  # Using slicing to reverse

# Example
print(reverse_string("hello"))  # Output: "olleh"
```

---

## 2. Find Factorial of a Number

### Problem:
Given a number `n`, find its factorial.

### Approach:
- Use recursion or an iterative approach to compute factorial.

### Solution:
```python
def factorial(n):
    if n == 0 or n == 1:
        return 1
    return n * factorial(n - 1)

# Example
print(factorial(5))  # Output: 120
```

---

## 3. Find the Greatest Common Divisor (GCD)

### Problem:
Find the GCD of two numbers `a` and `b`.

### Approach:
- Use Euclidean algorithm for efficient computation of GCD.

### Solution:
```python
def gcd(a, b):
    while b:
        a, b = b, a % b
    return a

# Example
print(gcd(8, 12))  # Output: 4
```

---

## 4. Check if a String is a Palindrome

### Problem:
Check if a given string is a palindrome.

### Approach:
- Compare the string with its reverse.

### Solution:
```python
def is_palindrome(s):
    return s == s[::-1]

# Example
print(is_palindrome("madam"))  # Output: True
```

---

## 5. FizzBuzz Problem

### Problem:
Print numbers from 1 to 100. For multiples of 3, print "Fizz"; for multiples of 5, print "Buzz"; for multiples of both, print "FizzBuzz".

### Approach:
- Use conditional statements for multiples.

### Solution:
```python
def fizzbuzz(n):
    for i in range(1, n+1):
        if i % 3 == 0 and i % 5 == 0:
            print("FizzBuzz")
        elif i % 3 == 0:
            print("Fizz")
        elif i % 5 == 0:
            print("Buzz")
        else:
            print(i)

# Example
fizzbuzz(15)
```

---

## 6. Find the Maximum Subarray Sum (Kadane’s Algorithm)

### Problem:
Find the maximum sum of a contiguous subarray in a given array.

### Approach:
- Use Kadane’s algorithm, which is efficient with a time complexity of O(n).

### Solution:
```python
def max_subarray_sum(arr):
    max_current = max_global = arr[0]
    for num in arr[1:]:
        max_current = max(num, max_current + num)
        if max_current > max_global:
            max_global = max_current
    return max_global

# Example
print(max_subarray_sum([-2, 1, -3, 4, -1, 2, 1, -5, 4]))  # Output: 6
```

---

## 7. Find Prime Numbers up to `n` (Sieve of Eratosthenes)

### Problem:
Find all prime numbers up to a given number `n`.

### Approach:
- Use the Sieve of Eratosthenes for efficient prime number generation.

### Solution:
```python
def sieve_of_eratosthenes(n):
    primes = [True for _ in range(n+1)]
    p = 2
    while p * p <= n:
        if primes[p]:
            for i in range(p * p, n+1, p):
                primes[i] = False
        p += 1
    return [p for p in range(2, n+1) if primes[p]]

# Example
print(sieve_of_eratosthenes(30))  # Output: [2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
```

---

## 8. Merge Two Sorted Arrays

### Problem:
Given two sorted arrays, merge them into one sorted array.

### Approach:
- Use two pointers to merge the arrays.

### Solution:
```python
def merge_sorted_arrays(arr1, arr2):
    result = []
    i, j = 0, 0
    while i < len(arr1) and j < len(arr2):
        if arr1[i] < arr2[j]:
            result.append(arr1[i])
            i += 1
        else:
            result.append(arr2[j])
            j += 1
    result += arr1[i:]
    result += arr2[j:]
    return result

# Example
print(merge_sorted_arrays([1, 3, 5], [2, 4, 6]))  # Output: [1, 2, 3, 4, 5, 6]
```

---

## 9. Count Occurrences of Each Element in an Array

### Problem:
Given an array, count the occurrences of each element.

### Approach:
- Use a dictionary to store and count occurrences.

### Solution:
```python
def count_occurrences(arr):
    count = {}
    for num in arr:
        if num in count:
            count[num] += 1
        else:
            count[num] = 1
    return count

# Example
print(count_occurrences([1, 2, 2, 3, 1, 4]))  # Output: {1: 2, 2: 2, 3: 1, 4: 1}
```

---

## 10. Find Missing Number in an Array

### Problem:
Given an array containing `n-1` integers between `1` and `n`, find the missing number.

### Approach:
- Use the sum formula: Sum of first `n` numbers is `n*(n+1)//2`.

### Solution:
```python
def find_missing_number(arr, n):
    total_sum = n * (n + 1) // 2
    return total_sum - sum(arr)

# Example
print(find_missing_number([1, 2, 4, 5, 6], 6))  # Output: 3
```

---

### Tips for Advanced Coding:
1. **Understand the Problem**: Break it down before coding.
2. **Optimize Your Code**: Aim for lower time and space complexity.
3. **Practice Recursion**: It's important in many advanced problems.
4. **Use Data Structures Efficiently**: Arrays, linked lists, trees, and hashmaps should be your tools of choice.
5. **Debug**: Be methodical in identifying issues in your logic.

This detailed markdown will help you cover some of the fundamental and advanced coding questions you may encounter during the TCS NQT. Each question provides a short method description to help you understand how to solve it.
