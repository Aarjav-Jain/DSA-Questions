# [Majority Element](https://leetcode.com/problems/majority-element/)

## Method 1 (Brute Force)

Find the frequency of every element by using linear search.<br>
Time Complexity - O(n<sup>2</sup>)

We can optimise this solution by sorting the elements and using Binary Search.<br>
Time Complexity - O(n log n)

## Method 2 (By using a HashMap)

We can reduce the time complexity to O(n) by using a extra space to store the frequency of every element.<br>
And then checking which element has frequency greater than n/2.<br>
Time Complexity - O(n)<br>
Space Complexity - O(n)

---

## Moore's Voting Algorithm

Moore's Voting Algorithm works in two phases : the first phase find a candidate which <u>could</u> have frequency more than n/2.<br>
Then we check if our candidate is actually majority by calculating the frequency of the element by linear search.

**NOTE:** This algorithm does not guarantee the first occurence.

```C++
int findMajority(int ar[],int n){

    // PHASE 1: finding the possible candidate
    int res = 0,count = 1;
    for(int i = 1; i < n; ++i){
        if(ar[res] == ar[i])
            ++count;
        else
            --count;
        if(count == 0){
            res = i;
            count = 1;
        }
    }

    // PHASE 2: checking if the candidate if actually majority
    count = 0;
    for(int i=0; i < n; ++i){
        if(ar[res] == ar[i])
            ++count;
    }

    if(count <= n/2)
        return -1;

    return ar[res];
}
```
