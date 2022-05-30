# [Searching in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

## Method 1

To solve this problem we will divide the array into 2 parts from the minimium element(first we need to find the minimum element) and then search the required element in both the arrays.

The two arrays will be <u>0 to index of (minimum element) - 1</u> and <u>index of (minimum element) till n-1</u>.

Time Complexity : O(3logn) ~ O(logn)

## Method 2(More Optimised)

We have made simple conditions according to if the required element would be in the greater or smaller array.

Time Complexity : O(logn)

```C++
int search(vector<int>& nums, int target) {
    int n = nums.size();
    int s = 0;
    int e = n-1;

    while(s<=e){
        int mid = (s+e)/2;
        if(nums[mid] == target)
            return mid;

        if(nums[0] <= target){
            if(nums[0] <= nums[mid]){
                if(nums[mid] < target)
                    s = mid + 1;
                else
                    e = mid - 1;
            }
            else
                e = mid - 1;
        }

        else{
            if(nums[0] > nums[mid]){
                if(nums[mid] < target)
                    s = mid + 1;
                else
                    e = mid - 1;
            }
            else
                s = mid + 1;
        }
    }
    return -1;
}
```
