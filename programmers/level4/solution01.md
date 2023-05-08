# 프로그래머스 Level4 : 올바른 괄호의 갯수

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/12929)

## Stack
```java
import java.util.*;
class Solution {
    class P{
        int open, close;
        P(int open, int close){
            this.open = open;
            this.close = close;
        }
    }
    public int solution(int n) {
        int answer = 0;
        Stack<P> stack = new Stack<>();
        stack.push(new P(0,0));
        while(!stack.isEmpty()){
            P p = stack.pop();

            if(p.open > n) continue;
            if(p.open < p.close) continue;
            if(p.open + p.close == 2*n){
                answer++;
                continue;
            }

            stack.push(new P(p.open+1, p.close));
            stack.push(new P(p.open, p.close+1));
        }

        return answer;
    }
}
```

## Queue
```java
import java.util.*;
class Solution {
    int cnt = 0;
    boolean checkParentheses(String pstr){
        Queue<Character> queue = new LinkedList<>();
        for(char c : pstr.toCharArray()){
            if(c=='('){
                queue.offer('(');
            }else {
                if(!queue.isEmpty()&&queue.peek()=='('){
                    queue.poll();
                }else {
                    return false;
                }
            }
        }
        if(queue.isEmpty()) return true;
        return false;
    }
    void makeParentheses(int n, int open, int close, String pstr){
        if(open==n && close==n){
            if(checkParentheses(pstr)){
                cnt++;
            } 
        } else{
            if(open<n) makeParentheses(n,open+1,close,pstr+"(");
            if(open>=close && close<n) makeParentheses(n,open,close+1,pstr+")");
        }
    }
    public int solution(int n) {
        makeParentheses(n,0,0,"");
        return cnt;
    }
}
```