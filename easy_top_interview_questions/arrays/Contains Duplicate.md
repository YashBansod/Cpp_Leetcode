# Contains Duplicate

## Problem Statement:

- Given an array of integers, find if the array contains any duplicates.

  Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.
  
  
  
  **Example 1:**
  
  ```
  Input: [1,2,3,1]
  Output: true
  ```
  
  
  
  **Example 2:**
  
  ```
  Input: [1,2,3,4]
  Output: false
  ```
  
  
  
  **Example 3:**
  
  ```
  Input: [1,1,1,3,3,4,3,2,4,2]
  Output: true
  ```

## Solution:

#### Attempt 1:

First sort the array, then compare consecutive elements for duplicates.

```c++
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        std::sort(nums.begin(), nums.end());
        for(int i=1; i<nums.size(); ++i){
            if(nums[i-1] == nums[i]) return true;
        }
        return false;
    }
};
```

| Status                                                       | Runtime | Memory  | Language |
| :----------------------------------------------------------- | :------ | :------ | :------- |
| [Accepted](https://leetcode.com/submissions/detail/335977652/) | 56 ms   | 15.5 MB | cpp      |



#### Attempt 2:

Transfer the contents of the vector iteratively to an unordered set. Before insertion, check if the key is already present.

```c++
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_set<int> hashset; 
        for (int key : nums) { 
            if (hashset.find(key) != hashset.end()) { return true; }       
            hashset.insert(key); 
        } 
        return false;        
    }
};
```

| Status                                                       | Runtime | Memory  | Language |
| :----------------------------------------------------------- | :------ | :------ | :------- |
| [Accepted](https://leetcode.com/submissions/detail/335978937/) | 72 ms   | 20.1 MB | cpp      |

<!---

​	Author: Yash Bansod

-->