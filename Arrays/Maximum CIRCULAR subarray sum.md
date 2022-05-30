# [Maximum Circular Subarray Sum](https://leetcode.com/problems/maximum-sum-circular-subarray/submissions/)

## THEORY

- <u>next element</u> in an circular array is **( i + 1 ) % n**
- <u>previous element</u> in an circular array is **( i - 1 + n ) % n**

## Method 1 (Brute Force)

```C++
int maxCircularSum(int ar[], int n) {
	int res = ar[0];
	for (int i = 0; i < n; ++i) {
		int sum = ar[i];
		for (int j = (i + 1) % n; j != i; j = (j + 1) % n) {
			sum += ar[j];
			res = max(sum, res);
		}
	}
	return res;
}
```

## Method 2 (Optimised Solution)

The idea is to use kadane's algorthim to find the max subarray sum in a non-circular array and to compare it with max subarray sum in a circular array.

Now, to find the max-subarray sum in a circular subarray <u>we can subtract the minimun subarray sum with the total sum of the array.</u>

```C++
int kadaneAlgorithm(int ar[],int n,bool b = true){
    int curMaxSum = ar[0];
    int maxSum = ar[0];
    int curMinSum = ar[0];
    int minSum = ar[0];
    for(int i=1;i<n;++i){
        curMaxSum = max(curMaxSum + ar[i], ar[i]);
        maxSum = max(curMaxSum,maxSum);
        curMinSum = min(curMinSum + ar[i], ar[i]);
        minSum = min(curMinSum,minSum);
    }

    if(!b)
        return minSum;
    return maxSum;
}

int maxCircularSum(int ar[], int n) {
	int maxNormalSum = kadaneAlgorithm(ar,n);

    // if maxNormalSum is negative it means that all numbers are negative there the minimum negative no will be max sum, therefore there is no sense to check for circular subarray sum.

    if(maxNormalSum < 0)
        return maxNormalSum;

    int minSubarraySum = kadaneAlgorithm(ar,n,false);

    int sum = 0;
    for(auto i : ar)
        sum += i;

    return max(maxNormalSum,sum-minSubarraySum);
}
```
