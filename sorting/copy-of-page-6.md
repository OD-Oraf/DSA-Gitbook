# Python Sorting

## Sorting

1. `sort_words(words: List[str]) -> List[str]` - This function accepts a list of words and returns a new list of words sorted based on their length, in _descending order_.
2. `sort_numbers(numbers: List[int]) -> List[int]` - This function accepts a list of numbers and returns a new list of numbers sorted based on their absolute value, in _ascending order_. Hint: You may use the `abs()` function to get the absolute value of a number.

```python
from typing import List

def get_word_length(word: str) -> int:
    return len(word)

def get_abs_value(num: int) -> int:
    return abs(num)

def sort_words(words: List[str]) -> List[str]:
    words.sort(key=get_word_length, reverse=True)
    return words


def sort_numbers(numbers: List[int]) -> List[int]:
    numbers.sort(key=get_abs_value)
    return numbers

```
