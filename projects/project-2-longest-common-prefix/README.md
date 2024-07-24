# Project: Longest Common Prefix

## Problem 1

Write a function `longest_common_prefix` that takes a list of strings as input and returns the longest common prefix of the strings. If there is no common prefix, the function should return an empty string.

### Example

```python
words = ["flower", "flow", "flight"]

print(longest_common_prefix(words))  # "fl"

words = ["dog", "racecar", "car"]

print(longest_common_prefix(words))  # ""

words = ["apple", "app", "application"]

print(longest_common_prefix(words))  # "app"
```

## Problem 2

Modify the function to handle an arbitrary number of input strings.

### Example

```python
print(longest_common_prefix("flower", "flow", "flight", "flour"))  # "fl"

print(longest_common_prefix("dog", "racecar", "car"))  # ""

print(longest_common_prefix("apple", "app", "application", "apartment"))  # "app"
```
