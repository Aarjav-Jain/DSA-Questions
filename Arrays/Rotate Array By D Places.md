refer :- https://www.techiedelight.com/left-rotate-array-c/

Refer:- https://leetcode.com/problems/move-zeroes/

## Method 1 (Rotating the array d times)

The most naive method to solve the problem is:<br>
Rotating the array by one, d-times.

### Time Complexity : O(nd)

### Auxillary Space : O(1)

---

## Method 2 (By Using Extra Space)

Store the first D - elements in a temparary array and rotate accordingly.(By Observation)

```C++
void rotate(int ar[],int d,int n) {

    // if d>n then d = d-n (by observation)
    d = (d>=n) ? d%n : d;

    // store the first d elements in a temp array
    int temp[d];
    for(int i=0;i<n;++i){
		cin>>ar[i];
		if(i<d)
			temp[i] = ar[i];
	}

    // rotate the first n-d+1 elements accordingly
	for(int i=0;i<n-d;++i){
		ar[i] = ar[i+d];
	}

    // now place the stored elements according to the rotation
	for(int i=n-d;i<n;++i){
		ar[i] = temp[i-n+d];
	}

	for(int i :ar)
		cout<<i<<" ";
}
```

### Time Complexity : O(n)

### Auxillary Space : O(d)

## Method 3 (Reversing the Array)

(Trick based)<br>

1. Rotate the first 'd' elements.
2. Rotate the remaning 'n-d' elements.
3. Rotate the full array.

```C++
void reverse(int ar[],int d,int n){
    int s = 0;
    int e = n-1;
    while(s<e){
        swap(ar[s],ar[e]);
        ++s;
        --e;
    }
}

void rotate(int ar[],int d,int n) {
     // if d>n then d = d-n (by observation)
    d = (d>=n) ? d%n : d;

    //Rotate first d elements
    reverse(ar,0,d-1);

    //Rotate remaining elements
    reverse(ar,d,n-1);

    //Rotate the full array
    reverse(ar,0,n-1);
}
```
