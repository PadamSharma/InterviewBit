# Balanced Parantheses!

![](https://img.shields.io/badge/Easy-neon?style=for-the-badge)
![](https://img.shields.io/badge/Amazon,Google-blue?style=for-the-badge)

Given a string A consisting only of '(' and ')'.

You need to find whether parantheses in A is balanced or not ,if it is balanced then return 1 else return 0.

> Iterate through the string and if '(' appears then push it into the stack else for ')', check whether stack is empty or not, as if stack is empty then the string can never be balanced as there is no opening paranthesis. If the stack is not empty then pop from stack as there is no possibilty of ever encountering closing b during popping, thus we can be sure that popping occurs for opening b only. Finally check if stack does not contain any opening b, return emptyness of the stack.

```c++
int Solution::solve(string A) {
    stack<int> st;
    if(A[0]==')'){
        return 0;
    }
    for(auto i:A){
        if(i=='('){
            st.push(i);
        }
        else{
            if(st.empty()){
                return 0;
            }
            st.pop();
        }
    }
    return st.empty();
}

```