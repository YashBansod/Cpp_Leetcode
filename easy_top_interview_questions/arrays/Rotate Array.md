# Rotate Array

## Problem Statement:

Given an array, rotate the array to the right by *k* steps, where *k* is non-negative.

**Follow up:**

- Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.
- Could you do it in-place with O(1) extra space?



**Example 1:**

```
Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
```



**Example 2:**

```
Input: nums = [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
```



**Constraints:**

- `1 <= nums.length <= 2 * 10^4`

- It's guaranteed that `nums[i]` fits in a 32 bit-signed integer.

- `k >= 0`

  

## Solution:

#### Attempt 1:

Insert the k last elements to the front of the vector and remove from the back of the vector

```c++
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        
        if(k >= nums.size()) k -= nums.size();
        
        if(k > 0){
            for(int i=0; i<k; ++i){
                nums.insert(nums.begin(), nums[nums.size() - 1]);
                nums.pop_back();
            }
        }
        
    }
};
```

| Status                                                       | Runtime | Memory | Language |
| :----------------------------------------------------------- | :------ | :----- | :------- |
| [Accepted](https://leetcode.com/submissions/detail/335974227/) | 304 ms  | 9.9 MB | cpp      |



#### Attempt 2:

Insert the k last elements to the front of the vector and remove from the back of the vector

(Optimized)

```c++
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        
        if(k >= nums.size()) k %= nums.size();
        
        if(k > 0){
            
            nums.insert(nums.begin(), k, 0);
            vector<int>::iterator move_from = nums.end() - k, move_to = nums.begin();
            
            while(move_from != nums.end()){
                *move_to++ = std::move(*move_from++);
            }
            nums.erase(nums.end() - k, nums.end());
        }
        
    }
};
```

| Status                                                       | Runtime | Memory | Language |
| :----------------------------------------------------------- | :------ | :----- | :------- |
| [Accepted](https://leetcode.com/submissions/detail/335975397/) | 8 ms    | 9.9 MB | cpp      |



#### Attempt 3:

First Reverse the (0 -> (End - k)) indices of the array. Then reverse the entire array. Then reverse the (0 -> k) indices of the array.

```c++
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
            k%=nums.size();
            reverse(nums.begin(),nums.end()-k);
            reverse(nums.begin(),nums.end());
            reverse(nums.begin(),nums.begin()+k);
    }
};
```

| Status                                                       | Runtime | Memory | Language |
| :----------------------------------------------------------- | :------ | :----- | :------- |
| [Accepted](https://leetcode.com/submissions/detail/335976613/) | 8 ms    | 9.9 MB | cpp      |



<!---

​	Author: Yash Bansod

-->