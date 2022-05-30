# Prefix Sum Technique

PrefixSum technique is used to store the cumulative sum of an array.

```C++
void prefixSum(int ar[],int n){
    int prefixSum[n];
    prefixSum[0] = ar[0];
    for(int i=0;i<n;++i){
        prefixSum[i] = prefixSum[i-1] + ar[i];
    }
}
```

```
INPUT: 2 8 3 9 6 5 4
OUTPUT: 2 10 13 22 28 33 37
```

## Q1) Given n ranges, find the maximum appearing element in these ranges.(0<= L[i],R[i] <1000)

---

In Brute Force Method we will travese through every range and increment the frequency of element by using a frequency array, (since the value of elements is less than 1000.)<br>
And then, iterate over the array to find the max occuring elements.

## Trick Method

The trick is that we will not iterate over all the elements in the range instead we will increase the value of L[i] and decrease the value of the element to next of R[i] i.e (R[i]+1).

Then we find the prefix sum of the array to find the final freqeucy of all the elements and then return the index of the maximum frequency.

```C++
int maxOcc(int l[],int r[],int n){

    vector<int> v(1000,0);

    for(int i = 0; i < n; ++i){
        v[l[i]]++;
        v[r[i] + 1]--;
    }

    int maxm = arr[0], res = 0;

    for(int i = 1; i < n; ++i){
        v[i] += v[i-1];
        if(maxm < v[i]){
            maxm = v[i];
            res = i;
        }
    }
}
```
