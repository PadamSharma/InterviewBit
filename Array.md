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

---
title: New Issue
labels: bug, enhancement
---
<!--#
NOUN=mother
ATTRIBUTION=Mark Wahlberg
$-->

"Say hi to your {{ NOUN }} for me," {{ ATTRIBUTION }}

![](https://img.shields.io/badge/xxx-blue?style=for-the-badge)
![](https://img.shields.io/badge/xxx-neon?style=for-the-badge)
![](https://img.shields.io/badge/xxx-yellow?style=for-the-badge)
![](https://img.shields.io/badge/xxx-red?style=for-the-badge)


[I'm an inline-style link](https://www.somewebsite.com)

[I'm an inline-style link with title](https://www.somewebsite.com "somewebsite's Homepage")

[I'm a reference-style link][Arbitrary case-insensitive reference text]

[I'm a relative reference to a repository file](../blob/master/LICENSE)

[You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself]

Some text to show that the reference links can follow later.

[arbitrary case-insensitive reference text]: https://www.somewebsite.org
[1]: http://somewebsite.org
[link text itself]: http://www.somewebsite.com