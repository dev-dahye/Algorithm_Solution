# 프로그래머스 Level1 : 월간 코드 챌린지 시즌1 3진법 뒤집기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/68935)

```java
import java.util.Stack;
class Solution {
    public int solution(int n) {
        int answer = 0;
        Stack<Integer> stack = new Stack<>();
        
        while(n!=0){
            stack.push(n % 3);
            n /= 3;
        }
        
        int pow = 0;
        while(!stack.empty()){
            answer += stack.pop() * Math.pow(3,pow);
            pow++;
        }
        
        return answer;
    }
}
```