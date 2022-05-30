refer:- https://www.geeksforgeeks.org/minimum-group-flips-to-make-binary-array-elements-same/

## Method 1 ( Naive :- O(2n) )

The idea is to count no of flips required tomake 0 to 1 and 1 to 0 in 1st loop.<br>
Then find which requires minimum no of flips and then print the occurences in second loop.

```C++
void printGroups(int ar[],int n){
    int zero = 0,one = 0;
    int prev = ar[0];
    for(int i=0;i<n;++i){
        if(ar[i] != prev){
            if(prev == 0)
                ++zero;
            else
                ++one;
        }
    }
    // for handling the last element
    if(prev == 0)
    	++zero;
    else
    	++one;

    int minm = min(zero,one);
    int start = -1;
    for(int i=0;i<n;++i){
        if(ar[i] == minm){
            if(start == -1){
                start = i;
                cout<<start<<" ";
            }
        }
        else{
            if(start != -1)
                cout<<i-1<<endl;
            start = -1;
        }
    }

    //for handling corner case like : 0 0 0 0
    if(start == -1)
        cout<<n-1<<endl;
}
```

## Method 2 (TRICK BASED)

By observation we can find that <br>
a) The max difference between 0's and 1's can be atmost equal to 1.<br>
e.g. 110011001<br>
So, by observation **the second set of group will always be less in no.**

b) If the first element != last element then the no of clusters of 0 and 1 are same.<br>
e.g. 10001001100

### Algorithm

When a[0] == a[n-1] then minimum no of groups will be for the element other than a[0].

When a[0] != a[n-1] then no of groups for both the elements will be equal.

```C++
void printGroups(int ar[],int n){

    int minm = 0;

    if(ar[0] == ar[n-1]){
        if(ar[0] == 1)
            minm = 0;
        else
            minm = 1;
    }

    int start = -1;

    for(int i=0;i<n;++i){
        if(ar[i] == minm){
            if(start != -1)
                start = i;
            cout<<start<<" ";
        }
        else{
            if(start != -1)
                cout<<i-1<<endl;
            start = -1;
        }
    }

    //for handling corner case like : 0 0 0 0
    if(start == -1)
        cout<<n-1<<endl;
}

```

## Sandeep Sir's Code

```C++
void printGroups(int ar[],int n){
    for(int i=1;i<n;++i){
        if(ar[i] == ar[i-1]){
            if(ar[i] != ar[0])
                cout<<i<<" ";
            else
                cout<<i-1<<endl;
        }
    }
    if(ar[n-1] == ar[0])
        cout<<(n-1)<<endl;
}
```
