# [Maximum Subarray Sum](https://leetcode.com/problems/maximum-subarray/)

## Brute Force O(n<sup>2</sup>)

We check the maximum possibe sum among all possible subarrays by making 2 loops.

## Kadane's Algorithm(optimal)

```C++
int maxSubArray(vector<int>& nums) {
        int n = nums.size();
        int sum = nums[0];
        int maxm = nums[0];
        for(int i=1;i<n;++i){
 // if (sum + current_element) < current_element then we take a new subarray starting from current_element for optimal result
            sum = max(sum+nums[i],nums[i]);
            maxm = max(maxm,sum);
        }
        return maxm;
    }
```

Other way to understand this is that we the curr sum = 0 as soon the sum gets negative.

```C++
        int sum=0;
        int ans=INT_MIN;
        for(int i=0;i<nums.size();i++)
        {
            sum+=nums[i];
            ans=max(ans,sum);
            if(sum<0)
                sum=0;
            // sum = 0 for starting a newsubrray
        }

        return ans;
```
