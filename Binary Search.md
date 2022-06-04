# Smaller or equal elements
```diff
+ very easy
```

Given an sorted array A of size N. Find number of elements which are less than or equal to B.

NOTE: Expected Time Complexity O(log N)

> If left == right then terminate the loop. Left is the index of the element just less than or equal to B while right is the element greater than B. If left == right then the element is definitely either equal to B (last index of that duplicate element) or just greater than B.

```c++
int Solution::solve(vector<int> &A, int B) {
    int l = 0, r = A.size();
    while(l < r){
        int mid = (l + r) / 2;
        if(A[mid] <= B){
            l=mid+1;
        }
        else{
            r=mid;
        }
    }
    return r;
}
```

#

```diff
+
```

```c++

```