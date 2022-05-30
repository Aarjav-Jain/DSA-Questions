# [Find the no of times a Sorted array is Rotated](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

By observation the no of times a sorted array is rotated is equal to the index of the smallest element.

No. of times array is rotated is equal to:-

- **index of smallest element (anti-clockwise)**
- **(n - index of smallest element) (clockwise)**

```C++
    int findMin(vector<int>& nums) {

        int n = nums.size();

        if(nums[0] <= nums[n-1])
            return nums[0];

        int s = 0;
        int e = n-1;
        int index = 0;
        while(s<=e){
            int mid = (s+e)/2;

            // if nums[0] <= nums[mid] then we are in larger part of the array, therefore we do s = mid+1
            if(nums[0] <= nums[mid])
                s = mid + 1;

            // if nums[mid] < nums[0] this means we are in the smallest side of the array hence we store the ans in a variable and if there is any other smaller value possible.
            else{
                index = mid;
                e = mid-1;
            }
        }
        return index;

    }
```
