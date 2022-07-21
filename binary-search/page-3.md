# 14. Classical Binary Search

Given a target integer T and an integer array A sorted in ascending order, find the index i such that A\[i] == T or return -1 if there is no such index.

**Assumptions**

* There can be duplicate elements in the array, and you can return any of the indices i such that A\[i] == T.



* The input is the sorted array, so we can use the binary search to find the index of target.&#x20;
* TC: O(logn)
* SC: O(1)

```java
public int binarySearch(int[] array, int target) {
    if (array == null || array.length == 0) {
        return -1;
    }
    
    int left = 0;
    int right = array.length - 1;
    
    while (left <= right) {
        int middle = left + (right - left) / 2;
        if (array[middle] == target) {
            return middle;
        } else if (array[middle] < target) {
            left++;
            
        } else {
            right--;
        }
    }
    return -1;
}

```

