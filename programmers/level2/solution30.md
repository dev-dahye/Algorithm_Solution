# 프로그래머스 Level2 : 월간 코드 챌린지 시즌2 괄호 회전하기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/76502)

```java
import java.util.Deque;
import java.util.LinkedList;
import java.util.Stack;

class Solution {
    public int solution(String s) {
        int len = s.length();
        Deque<Character> deque = new LinkedList<>(); 
        
        int cnt1 = 0;
        int cnt2 = 0;
        int cnt3 = 0;
        for(int i=0; i<len; i++){
            char c = s.charAt(i);
            if(c=='(') cnt1++;
            else if(c==')') cnt1--;
            else if(c=='[') cnt2++;
            else if(c==']') cnt2--;
            else if(c=='{') cnt3++;
            else cnt3--;
            deque.add(s.charAt(i));
        }
        if(cnt1!=0||cnt2!=0||cnt3!=0) return 0;
        
        int cnt = 0;
        label:for(int i=0; i<len; i++){
            Stack<Character> stack = new Stack<>();
            for(int j=0; j<len; j++){
                char c = deque.removeFirst();
                deque.addLast(c);

                if(c == '(' || c == '[' || c=='{') stack.push(c);
                else if(!stack.isEmpty()&&c==')'){
                    if(stack.peek()=='(') stack.pop();
                } else if(!stack.isEmpty()&&c==']'){
                    if(stack.peek()=='[') stack.pop();
                }
                else if(!stack.isEmpty()&&c=='}'){
                    if(stack.peek()=='{') stack.pop();
                } 
            }
            if(stack.isEmpty()) cnt++;
            deque.addFirst(deque.removeLast());
        }
        
        return cnt;
    }
}
```


<br>
<br>

- - -

## Reference
- <https://crazykim2.tistory.com/581>
- <https://docs.oracle.com/javase/7/docs/api/>