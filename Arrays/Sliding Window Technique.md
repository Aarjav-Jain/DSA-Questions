# Sliding Window Technique

## Q1) Given an array of integers and a number k, find the maximum sum of k consecutive elements.

---

## Optimal Method using Sliding Window Technique

The idea is to calculate the sum of first window i.e k elements and then adding the next element to the sum and subtracting the i-kth element.<br>
In this way we can stop doing the repetitive work and solve the question in O(n) time.

```C++
int maxKSubarraySum(int ar[],int k,int n){
    int sum = 0;
    for(int i=0;i<k;++i)
        sum += ar[i];

    int maxsum = 0;
    maxsum = max(maxsum,sum);

    for(int i=k;i<n;++i){
        sum += (ar[i] + ar[i-k]);
        maxsum == max(maxsum,sum);
    }

    return maxsum;
}
```

## Q2) First the first negative element in every window of size k. Print 0 if no negative no exists.

The idea is to save the negative elements in the first window and then shift the window by adding the ith element and subtracting the i-kth element.<br>
And we will add the ith element to the list if it is a negative no., and pop_front the i-kth element from the list if it is negative.

```C++
void firstNegative(int ar[],int n,int k){
    list<int> l;
    for(int i=0;i<n;++i){
        if(ar[i] < 0)
            l.push_back(ar[i]);
    }

    if(l.empty())
        cout<<0<<endl;
    else
        cout<<l.front();

    for(int i=k;i<n;++i){
        if(a[i] < 0)
            l.push_back(ar[i]);

        if(a[i-k]<0)
            l.pop_front();

        if(l.empty())
            cout<<0<<endl;
        else
            cout<<l.front();
    }
}
```

## Q3) [Find all Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)

```C++
bool check(vector<int>& v,vector<int>& t){
    for(int i=0;i<26;++i){
        if(v[i] != t[i])
            return false;
        }
    return true;
}

vector<int> findAnagrams(string s, string p) {
    int CHAR = 26;
    int n = s.size();
    int k = p.size();

    if(k > n)
        return {};

    vector<int> v(CHAR,0);
    vector<int> t(CHAR,0);
    vector<int> ans;

    for(int i=0;i<k;++i){
        v[s[i] - 'a']++;
        t[p[i] - 'a']++;
    }

    if(check(v,t))
        ans.push_back(0);

    for(int i=k;i<n;++i){
        v[s[i] - 'a']++;
        v[s[i-k] - 'a']--;
        if(check(v,t))
            ans.push_back(i-k+1);
        }

    return ans;
}
```

## Q4) Print all maximum nos in all subarrays of size k

The idea is to store all the maximums in a window in decreasing order and slide the window.

```C++
void maxKsize(int ar[],int n,int k){
    list<int> l;
    for(int i=0;i<k;++i){
        if(l.size() == 0){
            l.push_back(ar[i]);
        }

        else if(ar[i] > l.front()){
            l.clear();
            l.push_back(ar[i]);
        }

        else{
            while(ar[i] > l.back() && l.size()!=0)
                l.pop_back();
            l.push_back(ar[i]);
        }
    }

    for(int i=k;i<n;++i){
        if(ar[i-k] == l.front())
            l.pop_front();
        else if(ar[i] > l.front())
            l.clear();
        else{
            while(ar[i] > l.back() && l.size()!=0)
                l.pop_back();
        }
        l.push_back(ar[i]);
        cout<<l.front()<<endl;
    }
}
```

# Variable Size Sliding Window

## Q1) Given an array of <u>non - negative</u> integers. Find if there is a subarray with the given sum.

Here the start index of every element is denoted by s and the ending index is denoted by e. We increase the size of the window if the curr_sum < req_sum and decrease the window if curr_sum > req_sum.

```C++
    bool findSum(int ar[],int n,int sum){
        int curr_sum = ar[0];
        int s = 0;
        int e = 1;
        while(e<n && s<e){
            if(curr_sum > sum){
                curr_sum -= ar[s];
                s++;
            }
            if(curr_sum == sum)
                return true;
            curr_sum += ar[e];
        }

        // to check after adding the last element i.e ar[n-1]
        return (curr_sum == sum);
    }
```

**Note:-** <u>This approach only works for non-negative integers.</u>

## Longest Substring with k unique characters

We make a sliding window and store the encountered elements into a hashmap and check for the size of hashmap which represents the no of unique elements.

```C++
int longestSubstring(string s,int n,int k){
    map<char,int> m;
    int res = 0;
    int str=0,e=0;

    while(str<=e && e<n){
        if(m.size() == k){
            res = max(res,e - s + 1);
            m[s[e]]++;
            e++;
        }
        else if(m.size() > k){
            while(m.size() > k){
                m[s[str]]--;
                if(m[s[str]] == 0)
                    m.erase(s[str]);
                str++;
            }
        }
        else{
            m[s[e]]++
            e++;
        }
    }
    return res;
}
```

## Longest substring with all unique elements or no repeating elements

Now instead of checking for k we check the the size of the window is equal to the size of the hashmap.

```C++
int longestSubstring(string s,int n){
    map<char,int> m;
    int res = 0;
    int str=0,e=0;

    while(str<=e && e<n){
        if(m.size() == (e-s+1)){
            res = max(res,e - s + 1);
            m[s[e]]++;
            e++;
        }
        else if(m.size() < (e-s+1)){
            while(m.size() < (e-s+1)){
                m[s[str]]--;
                if(m[s[str]] == 0)
                    m.erase(s[str]);
                str++;
            }
        }
    }
    return res;
}
```

## [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)
