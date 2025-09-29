# List Comprehensions in Python

## 📋 Overview
List comprehensions provide a concise way to create lists in Python by applying an expression to each item in an iterable, optionally filtering items with a condition.

## 🎯 Purpose
- Create new lists from existing iterables
- Apply transformations and filters in a single line
- More readable and often faster than traditional loops

## 💡 Implementation

### Basic Syntax
```python
[expression for item in iterable if condition]
```

### Code Examples
```python
# Basic list comprehension
numbers = [1, 2, 3, 4, 5]
squares = [x**2 for x in numbers]
# Result: [1, 4, 9, 16, 25]

# With condition (filter)
even_squares = [x**2 for x in numbers if x % 2 == 0]
# Result: [4, 16]

# Nested list comprehension
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened = [item for row in matrix for item in row]
# Result: [1, 2, 3, 4, 5, 6, 7, 8, 9]

# With string manipulation
words = ['hello', 'world', 'python']
capitalized = [word.upper() for word in words if len(word) > 4]
# Result: ['HELLO', 'WORLD', 'PYTHON']
```

## 🔍 Key Points
- More Pythonic than traditional for loops
- Can include conditional logic for filtering
- Support nested iterations
- Can be used with any iterable (lists, tuples, strings, etc.)
- Should remain readable - avoid overly complex expressions

## 🔗 Related Topics
- [[Programming/Python/Dictionary Comprehensions]]
- [[Programming/Python/Generator Expressions]]
- [[Programming/Python/Filter and Map Functions]]

## 📚 References
- [Python Documentation - List Comprehensions](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions)

## 🏷️ Tags
`#python` `#concept` `#data-structures` `#comprehension`

---
*Created: 2024-01-15 | Last Updated: 2024-01-15*