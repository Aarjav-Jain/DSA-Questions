# [Peak Element](https://leetcode.com/problems/find-peak-element/)

Given an <u>unsorted</u> array find the element which is strictly greater than both its neighbour.

The trick here is to use binary search because by observation we see that we can divide the array into two parts.

Note:- Maximum element in a Bitonic/Mountain Array is equal to the PEAK ELEMENT.

```C++
int peakElement(int ar[],int n){
    int s = 0;
    int e = n-1;
    while(s<=e){
        if(mid == 0 && ar[mid] > ar[mid+1])
            return mid;
        if(mid == n-1 && ar[mid-1]<ar[mid])
            return mid;
        if(ar[mid] > ar[mid+1] && ar[mid-1] < ar[mid])
            return mid;
        else if(ar[mid] < ar[mid+1])
            s = mid+1;
        else
            e = mid-1;
    }
    return -1;
}
```
