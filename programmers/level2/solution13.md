# 프로그래머스 Level2 : 2017 팁스타운 짝지어 제거하기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12973)

```java
import java.util.Stack;
class Solution {
    public int solution(String s) {
        Stack<Character> stack = new Stack<>();
        
        for(char c : s.toCharArray()){
            if(!stack.isEmpty() && stack.peek()==c){
                stack.pop();
            } else{
                stack.push(c);
            }
        }
        
        if(stack.isEmpty()) return 1;
        return 0;
    }
}
```


## StringBuilder 효율성 테스트 시간초과
```java
class Solution
{
    public int solution(String s)
    {
        StringBuilder sb = new StringBuilder();
        sb.append(s);
        
        for(int i=0; i<sb.length(); i++){
            char c1 = sb.charAt(i);
            char c2 = i+1<sb.length()?sb.charAt(i+1):'0';
            
            if(c1==c2){
                sb.deleteCharAt(i);
                sb.deleteCharAt(i);
                i = i-2<0 ? -1:i-2;
            }
        }
        
        if(sb.length() == 0) return 1;
        return 0;
    }
}
```