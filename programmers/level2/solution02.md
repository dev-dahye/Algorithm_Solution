# 프로그래머스 Level2 : 올바른 괄호

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12909?language=java)

```java
import java.util.Stack;

class Solution {
    boolean solution(String s) {
        boolean answer = true;
        Stack<Character> stack = new Stack<>();
        
        for(char c : s.toCharArray()){
            if(c == '(')
                stack.push(c);
            else{
                if(stack.isEmpty()){
                    answer = false;
                    break;   
                }
                else
                    stack.pop();
            }
        }

        /*
        int l = s.length();
        for(int i=0; i<l; i++){
            if(s.charAt(i) == '('){
                stack.push('(');
            } else{
                if(stack.isEmpty()){
                    answer = false;
                    break;   
                }
                stack.pop();
            }
        }
        */
              
        if(!stack.isEmpty())
            answer = false;

        return answer;
    }
}
```