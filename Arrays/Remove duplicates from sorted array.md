# [Remove Duplicates from a Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

## Using Extra Space

### Method 1

By checking whether the current element is equal to the next element and adding the each element to a new array.

```C++
 int removeDuplicates(int ar[]) {
		int temp[n];
		int j = 0;

		for (int i = 0; i < n - 1; ++i) {
			if (ar[i] != ar[i + 1]) {
				temp[j] = ar[i];
				++j;
			}
		}

        temp[j] = ar[n - 1];

		for (int i = 0 ; i <= j; ++i)
			ar[i] = temp[i];

		return j;
}
```

### Method 2

By adding all elements to a set.

### Time Complexity : O(n)

### Auxillory Space: O(n)

---

## Using Constant Space

```C++
int removeDuplicates(int ar[]) {
    int res = 0;

	for (int i = 0; i <= n - 2; ++i) {
		if (ar[i] != ar[i + 1]) {
			ar[res + 1] = ar[i + 1];
			res++;
		}
	}
    return res;
}
```

### Time Complexity : O(n)

### Auxillory Space: O(1)
