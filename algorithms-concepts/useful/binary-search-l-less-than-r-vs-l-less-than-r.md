# Binary Search: l < r VS l <= r



* left < right
  * Good to use with an even number of elements and stop when pointers meet
  * Good to use for boundary conditions

```java
int left = 0, right = arr.length;
while (left < right) {
    int mid = left + (right - left) / 2;
    if (arr[mid] < target) {
        left = mid + 1;
    } else {
        right = mid;
    }
}
// At the end, 'left' points to the first element that is >= target
```

* left <= right
  * Needed when there are an odd number of elements and we need to make sure the middle element is processed
  * Good for finding exact match

```java
int left = 0, right = arr.length - 1;
while (left <= right) {
    int mid = left + (right - left) / 2;
    if (arr[mid] == target) {
        // Found the target
        break;
    } else if (arr[mid] < target) {
        left = mid + 1;
    } else {
        right = mid - 1;
    }
}
```
