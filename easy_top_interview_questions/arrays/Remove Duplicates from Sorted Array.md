# Remove Duplicates from Sorted Array

## Problem Statement:

Given a sorted array *nums*, remove the duplicates [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) such that each element appear only *once* and return the new length.



Do not allocate extra space for another array, you must do this by **modifying the input array [in-place](https://en.wikipedia.org/wiki/In-place_algorithm)** with O(1) extra memory.



**Example 1:**



```
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.

It doesn't matter what you leave beyond the returned length.
```



**Example 2:**



```
Given nums = [0,0,1,1,1,2,2,3,3,4],

Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively.

It doesn't matter what values are set beyond the returned length.
```



**Clarification:**



Confused why the returned value is an integer but your answer is an array?



Note that the input array is passed in by **reference**, which means modification to the input array will be known to the caller as well.



Internally you can think of this:



```
// nums is passed in by reference. (i.e., without making a copy)
int len = removeDuplicates(nums);

// any modification to nums in your function would be known by the caller.
// using the length returned by your function, it prints the first len elements.
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```



## Solution:

#### Attempt 1:

If consecutive elements are same, then remove one of them.

```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        for(int i=1; i<nums.size(); ++i){
            if(nums[i - 1] == nums[i]) {
                nums.erase(nums.begin() + i);
                i -= 1;
            }
        }
        return nums.size();
    }
};
```

| Status                                                       | Runtime | Memory | Language |
| :----------------------------------------------------------- | :------ | :----- | :------- |
| [Accepted](https://leetcode.com/submissions/detail/316635193/) | 144 ms  | 7.7 MB | cpp      |



#### Attempt 2:

Use the [std::unique](https://en.cppreference.com/w/cpp/algorithm/unique) API.

```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        return std::unique(nums.begin(),nums.end()) - nums.begin();
    }
};
```

| Status                                                       | Runtime | Memory | Language |
| :----------------------------------------------------------- | :------ | :----- | :------- |
| [Accepted](https://leetcode.com/submissions/detail/316636619/) | 20 ms   | 7.6 MB | cpp      |



#### Attempt 3: (From Discussion Section)

Use the [std::unique](https://en.cppreference.com/w/cpp/algorithm/unique) and [std::distance](https://en.cppreference.com/w/cpp/iterator/distance) API.

```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
		// Unique gives the final index after removing all adjacent duplicates
		// Distance between begin and the final index gives the valid size
        return std::distance(nums.begin(), std::unique(nums.begin(), nums.end())) ;
    }
};
```

| Status                                                       | Runtime | Memory | Language |
| :----------------------------------------------------------- | :------ | :----- | :------- |
| [Accepted](https://leetcode.com/submissions/detail/313531170/) | 16 ms   | 9.4 MB | cpp      |



---



<!--

​	Author: Yash Bansod

-->