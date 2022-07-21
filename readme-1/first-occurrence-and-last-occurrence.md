# First Occurrence and Last Occurrence

The array is sorted, so we can use binary search to find the first occurrence of the target we want to look for and the last occurrence.

TC: O(logn)

SC: O(1)

```java
public int[] findFirstAndLast(int array, int target) {
    if (array == null || array.length == 0) {
    return new int[] {-1, -1};
    }
    
    int first = firstOccur(array, target);
    int last = lastOccur(array, target);
    return new int[] {first, last};
}

public int firstOccur(int[] array, int target) {
    int left = 0;
    int right = array.length - 1;
    while (left < right - 1) {
        int middle = left + (right - left) / 2;
        
        if (array[middle] >= target) { // array[middle] <= target
            right = middle;   left = middle;
        } else {
            left = middle;
        }
    }
    
    if (array[left] == target) { // for last occurence check right side
        return left;
    } 
    if (array[right] == target) {
        return right;
    }
    return -1;
}
```
