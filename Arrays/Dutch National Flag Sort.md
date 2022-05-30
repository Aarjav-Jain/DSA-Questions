# [Dutch National Flag Sort](https://leetcode.com/problems/sort-colors/)

## Method 1(Naive)

Use STL sort function.

### Time Complexity : O(n logn)

### Auxillary Space : O(1)

## Method 2 (O(2n))

Count all occurences of zero's,one's and two's in O(n) complexity.<br>
And then modify the array accordingly also in O(n) complexity.

## Method 3 (Dutch National Flag Sort)

The idea is to have 3 pointers:-<br>
a) low -> representing the starting of 1's and end of 0's.<br>
b) mid -> representing the end of 1's and starting of unknowns.<br>
c) high -> representing the end of unknowns.

![Image showing pointers](https://media.geeksforgeeks.org/wp-content/uploads/list4.jpg)

Then we check for the value of ar[mid]:-<br>
a) ar[mid] = 0 :- swap( ar[low], ar[mid] ), low++, mid++<br>
b) ar[mid] = 1 :- mid++<br>
c) ar[mid] = 2 :- swap( ar[mid], ar[high] ), high--;

```C++
void DNFSort(int ar[],int n){
    int low = 0,mid = 0,high = n-1;
    while(mid<=high){
        if(ar[mid] == 0){
            swap(ar[low],ar[mid]);
            ++low;
            ++mid;
        }
        else if(ar[mid] == 1){
            ++mid;
        }
        else{
            swap(ar[mid],ar[high]);
            --high;
        }
    }
}
```
