# Two Pointer Approach

Two Pointer Approach can be applied in sorted arrays and works in O(n) time.

# Q1) Given an <u>unsorted array</u> find a pair with sum equal to x.

## Method 1(Naive)

Run two loops and check for sum.<br>

### Time Complexity:- O(n<sup>2</sup>)<br>

### Space Complexity:- O(1)

## Method 2(Hashing)

In this method we will use a hashmap and check if an element of value ( k - ar[i] ) is present in the array. If the element is present then we have would the ans else we will insert the element in the loop.

```C++
bool findSum(int ar[],int n,int k){
    unordered_set<int> m;
    for(int i=0;i<n;++i){
        int req = k - ar[i];
        if(m.find(req) != m.end())
            return true;
        else
            m.insert(ar[i]);
    }
    return false;
}
```

### Time Complexity:- O(n)<br>

### Space Complexity:- O(n)

## Method 3(Two Pointer)

```C++
bool findSum(int ar[],int n,int k){
    int s = 0;
    int e = n-1;
    sort(ar,ar+n);
    while(s < e){
        if(ar[s] + ar[e] == k)
            return true;
        else if(ar[s] + ar[e] < k)
            s++;
        else
            e--;
    }
    return false;
}
```

### Time Complexity:- O(nlogn)<br>

### Space Complexity:- O(1)

---

# Q2) Given an sorted array find a pair with sum equal to x.

Directly apply two pointer approach.

### Time Complexity:- O(n)<br>

### Space Complexity:- O(1)

# Q3) Count pairs with given sum.

use a for loop to travese every element and then count occurences for (sum-ar[i]) by last_occurence - first_occurence. Remember to divide the ans by two because we will twice for each pair.
