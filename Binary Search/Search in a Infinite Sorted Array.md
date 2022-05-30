# Search in a Infinite Sorted Array

```C++
int searchInInfiniteArray(int ar[],int n,int k){
    int s = 0;
    int e = 1;
    while(ar[e] < k){
        s = e;
        e *= 2;
    }

    while(s <= e){
        int mid = (s + e)/2;
        if(ar[mid] == k)
            return mid;
        else if(ar[mid] > k)
            e = mid - 1;
        else
            s = mid + 1;
    }
    return -1;
}
```
