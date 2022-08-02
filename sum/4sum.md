# 4Sum

Determine if there exists a set of four elements in a given array that sum to the given target number.





For this problem, we can consider the problem more scaleable, the kSum problem.

When dealing with 3Sum, we can use 2 sum idea to solve the problem, so for 4 sum, we still use the 3sum to solve the problem, and then the 3sum question converts to 2 sum question.

We can use recursion to solve the question.&#x20;

**the base case:**

* k== 2, call 2Sum
* the smallest number remaining is greater than `target / k`
* Or the largest number remaining is smaller than `target / k`

**th recursion rule:**

k - 1 Sum



```java

public List<List<Integer>> fourSum(int[] nums, int target) {
    Arrays.sort(nums);
    return kSum(nums, target,0, 4);
}

public  List<List<Integer>> kSum(int[] nums, long target, int start, int k) {
    List<List<Integer>> res = new ArrayList();
    
    if ( start == nums.length) {
        return res;
    }
    
    long averageValue = target  / k;
    
    if ( nums[start] > averageValue || averageValue > nums[nums.length - 1]) {
        return res;
    }
    
    if (k == 2) {
        return twoSum(nums, target, start);
    }
    
    
    for (int i = start; i < nums.length; i++) {
        if (i == start|| nums[i - 1] != nums[i]) {
            List<List<Integer>> subsets = kSum(nums, target - nums[i], i+ 1, k - 1);
            for (List<Integer> subset : subsets) {
                res.add(new ArrayList<>(Arrays.asList(nums[i])));
                res.get(res.size() - 1).addAll(subset);
            }
        }
    }
    
    return res;
}
public List<List<Integer>> twoSum(int[] nums, long target, int start) {
    List<List<Integer>> res = new ArrayList();
    int first = start;
    int second = nums.length - 1;
    
    while ( first < second) {
        
        int sum = nums[first] + nums[second];
        
        if ( sum < target || (first  > start && nums[first] == nums[first - 1])) {
            first++;
        } else if ( sum > target || (second < nums.length - 1 && nums[second] == nums[second + 1])) {
            second --;
        } else {
            res.add(Arrays.asList(nums[first],nums[second]));
            first++;
            second--;
        }
    }
    
    return res;
}



```

