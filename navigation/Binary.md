---
layout: page
title: Binary Search HW Aarush Gowda Code Snippets
description: Homework submission for Binary Search problems using Python.
permalink: /binary/
---

# Binary Search Homework Submission

**Student:** Aarush Gowda  
**Email:** gowda.aarush@gmail.com

---

## Introduction

This notebook demonstrates key binary search concepts and applies them to several homework and popcorn hack problems. In these exercises, we will:

- Implement a standard binary search.
- Solve a series of binary search challenges:
  - **Homework Hack 1:** Find a target element in a rotated sorted array.
  - **Homework Hack 2:** Find the first and last occurrence of a target element in a sorted array.
  - **Homework Hack 3:** Find the smallest element greater than or equal to a given target.
  
Each section includes the code along with example usage and expected outputs.

---

## Popcorn Hack: Basic Binary Search Implementation

Below is a standard iterative binary search algorithm that works on a sorted list.

```python
def binary_search(arr, target):
    """
    Performs binary search on a sorted array.
    Returns a tuple of (index, value) if the target is found, otherwise (-1, None).
    """
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        print(f"Searching between indices {left} and {right}, middle index is {mid}, value at mid is {arr[mid]}")
        if arr[mid] == target:
            return mid, arr[mid]
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1, None

# Example usage:
arr = [1, 3, 5, 7, 9, 11, 13]
target = 3
index, value = binary_search(arr, target)
print(f"Target found at index {index}, value is {value}")  # Expected: index 1, value 3
```
### Homework Hack 1:
```python
def search_rotated(arr, target):
    """
    Searches for target in a rotated sorted array and returns its index.
    If target is not found, returns -1.
    """
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        # Identify the sorted half.
        if arr[left] <= arr[mid]:
            # Left half is sorted.
            if arr[left] <= target < arr[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:
            # Right half is sorted.
            if arr[mid] < target <= arr[right]:
                left = mid + 1
            else:
                right = mid - 1
    return -1

# Example usage:
rotated_arr = [4, 5, 6, 7, 0, 1, 2]
target = 1
print("Index of target in rotated array:", search_rotated(rotated_arr, target))
# Expected output: 5 (since 1 is at index 5)
```
### Homework Hack 2:
```python
def first_occurrence(arr, target):
    """
    Returns the first occurrence index of target in arr using binary search.
    If target is not found, returns -1.
    """
    left, right = 0, len(arr) - 1
    result = -1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            result = mid
            right = mid - 1  # search towards left for first occurrence
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return result

def last_occurrence(arr, target):
    """
    Returns the last occurrence index of target in arr using binary search.
    If target is not found, returns -1.
    """
    left, right = 0, len(arr) - 1
    result = -1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            result = mid
            left = mid + 1  # search towards right for last occurrence
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return result

def first_and_last(arr, target):
    """
    Returns a tuple (first_occurrence, last_occurrence) of target in arr.
    If target is not present, returns (-1, -1).
    """
    return (first_occurrence(arr, target), last_occurrence(arr, target))

# Example usage:
arr = [1, 2, 2, 2, 3, 4, 5]
target = 2
print("First and last occurrence of target:", first_and_last(arr, target))
# Expected output: (1, 3)
```
### Homework Hack 3:
```python
def lower_bound(arr, target):
    """
    Uses binary search to find the smallest element in arr that is 
    greater than or equal to target. Returns the element, or -1 if no 
    such element exists.
    """
    left, right = 0, len(arr) - 1
    answer = -1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] >= target:
            answer = arr[mid]
            right = mid - 1  # search left to find smaller candidate
        else:
            left = mid + 1
    return answer

# Example usage:
arr = [1, 3, 5, 7, 9, 11]
target = 8
print("Smallest element >= target:", lower_bound(arr, target))
# Expected output: 9
```