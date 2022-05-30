# [Trapping Rainwater Problem](https://leetcode.com/problems/trapping-rain-water/)

## Brute Force

Two main things are required for calculating the trapped water by each block i.e.<br>
a) max height of left block <br>
b) max height on right block <br>
These two will act as a boundary to hold water in the block.

```C++
int maxWaterTrapped(int ar[],int n){
    int res = 0;

    // we run the loop for i=1 to i=n-2 because there is no boundary to hold water on one side for i=0 and i=n.
    for(int i=1;i<=n-1;++i){


        // we inilisize lmax and rmax with ar[i] because if there is no elevation greater than itself for a block then the ans will automatically be zero/
        int lmax = ar[i];
        int rmax = ar[i];

        // find the max height on the left side
        for(int j=0;j<i;++j)
            lmax = max(lmax,ar[j]);

        // find the max height on the right side
        for(int j=i+1;j<n;++j)
            rmax = max(rmax,ar[j]);

        // now the stored water will be equal to the elevation of ith block - minimum elevation of left and right side, otherwise the water will overflow.
        res = res + (min(lmax,rmax) - ar[i]);
    }
    return res;
}
```

## Optimised

We can optimised the time complexity from O(n<sup>2</sup>) to O(n) by using extra space for calculating and storing the lmax and rmax value for each index.

```C++
int getTrappedWater(int ar[],int n){
    int lmax[n],rmax[n];
    int res = 0;

    lmax[0] = ar[0];
    rmax[n-1] = ar[n-1];

    for(int i=1;i<n;++i)
        lmax[i] = max(lmax[i-1],ar[i]);

    for(int i=n-2;i>=0;--i)
        rmax[i] = max(ar[i],rmax[i+1]);

    for(int i=1;i<n-1;++i)
        res = res + min(lmax[i],rmax[i]) - ar[i];

    return res;
}
```
