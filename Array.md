# Pascal Triangle

**Easy**

> **Asked In: Google, Amazon**

Given numRows, generate the first numRows of Pascal's triangle.

Pascal's triangle : To generate A[C] in row R, sum up A'[C] and A'[C-1] from previous row R - 1.

```c++

```vector<vector<int> > Solution::solve(int A) {
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