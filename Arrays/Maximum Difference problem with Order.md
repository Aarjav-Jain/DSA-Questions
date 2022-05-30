refer:- https://leetcode.com/problems/maximum-difference-between-increasing-elements/<br>
Best time to sell stock:-
https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

# Find max difference between a[j] & a[i] such that (j > i)

```C++
int maxDifference(int ar[],int n){
    int maxm = ar[1]-ar[0];
    int min_element = ar[0];
    for(int i=1;i<n;++i){
        maxm = max(maxm,ar[i] - min_element);
        min_element = min(min_element,ar[i]);
    }
    return res;
}
```
