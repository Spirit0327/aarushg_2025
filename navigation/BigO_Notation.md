---
layout: page
title: Big O Notation HW Aarush Gowda
description: Homework submission for Lists and Filtering using Python lists and Pandas.
permalink: /big/
---

# Big O Notation Submission
### O(1) – Constant Time
This function always runs in the same time, no matter how big the list is.


```python
def print_hello():
    print("Hello, world!")

# Example
print_hello()
```

### O(log n) – Logarithmic Time
This example keeps dividing the number by 2 until it becomes 1.
```python 
def divide_until_one(n):
    while n > 1:
        n = n // 2
        print(n)

# Example
divide_until_one(32)
```

### O(n) – Linear Time
This function prints every number from 1 to n.
```python
def print_numbers(n):
    for i in range(1, n + 1):
        print(i)

# Example
print_numbers(10)
```

### O(n²) – Quadratic Time
This function checks if any two elements in the list add up to 10.
```python
def has_sum_ten(lst):
    for i in lst:
        for j in lst:
            if i + j == 10:
                return True
    return False

# Example
print(has_sum_ten([1, 3, 7, 2, 5]))
```

