# Binary Search Template

[https://leetcode.com/discuss/study-guide/786126/Python-Powerful-Ultimate-Binary-Search-Template.-Solved-many-problems](https://leetcode.com/discuss/study-guide/786126/Python-Powerful-Ultimate-Binary-Search-Template.-Solved-many-problems)

```java
left, right = min(search_space), max(search_space) // could be [0, n], [1, n] etc. Depends on problem
    while left < right:
        mid = left + (right - left) / 2
        if condition(mid):
            right = mid
        else:
            left = mid + 1
    return left
```
