<!-- # Pascal Triangle

**Easy**

> **Asked In: Google, Amazon**

Given numRows, generate the first numRows of Pascal's triangle.

Pascal's triangle : To generate A[C] in row R, sum up A'[C] and A'[C-1] from previous row R - 1.

```c++
vector<vector<int>> Solution::solve(int A) {
    if(A==0){
        return {};
    }
    else if(A==1){
        return {{1}};
    }
    else if(A==2){
        return {{1},{1,1}};
    }
    else{
        vector<vector<int>> v = {{1},{1,1}}; 
        for(int i=2;i<A;i++){
            vector<int> a(i+1,1);
            for(int j=1;j<i;j++){
                a[j]=(v[i-1][j-1]+v[i-1][j]);
            }
            v.push_back(a);
        }
        return v;
    }
}
```

# Wave Array
**Easy**

> **Asked In: Google,Adobe,Amazon,Zoho**

Given an array of integers,  sort the array into a wave like array and return it, 

In other words, arrange the elements into a sequence such that  a1 >= a2 <= a3 >= a4 <= a5.....

```c++
vector<int> Solution::wave(vector<int> &A) {
    sort(A.begin(), A.end());
    for(int i=0;i<A.size()-1;i+=2){
        swap(A[i], A[i+1]);
    }
    return A;
}
```
#  -->

# **1. Array math** (10 Ques)

[![](https://img.shields.io/badge/github-blue?style=for-the-badge)](https://github.com/hamzamohdzubair/redant)
[![](https://img.shields.io/badge/book-blueviolet?style=for-the-badge)](https://hamzamohdzubair.github.io/redant/)
[![](https://img.shields.io/badge/API-yellow?style=for-the-badge)](https://docs.rs/crate/redant/latest)
[![](https://img.shields.io/badge/Crates.io-orange?style=for-the-badge)](https://crates.io/crates/redant)
[![](https://img.shields.io/badge/Lib.rs-lightgrey?style=for-the-badge)](https://lib.rs/crates/redant)