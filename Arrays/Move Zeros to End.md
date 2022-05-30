# [Move Zeros to the End](https://leetcode.com/problems/move-zeroes/)

## Method 1 (Brute Force)

By swapping the zero element to the next non zero element.

```C++
void moveZeroes(vector<int>& nums) {

    int n = nums.size();

    for(int i=0;i<n;++i){
        if(nums[i] == 0){
            for(int j=i+1;j<n;++j){
                if(nums[j] != 0){
                    swap(nums[j],nums[i]);
                    break;
                }
            }
        }
    }
}
```

### Time Complexity : O(n<sup>2</sup>)

### Auxillary Space : O(1)

---

## Method 2 (Optimised)

Maintain a pointer zero which stores the index of the leftmost zeroth element and swaps accordingly;

```C++
int removeDuplicates(vector<int>& nums) {
    int zero = 0;
    int n = nums.size();
    for(int i=0;i<n;++i){
        if(nums[i] != 0){
            swap(nums[i],nums[zero]);
            zero++;
        }
    }
}
```

### Time Complexity : O(n)

### Auxillary Space : O(1)
