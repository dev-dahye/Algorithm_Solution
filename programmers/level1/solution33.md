# 프로그래머스 Level1 : 연습문제 문자열 다루기 기본

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12918)

```java
import java.util.regex.Pattern;

class Solution {
    public boolean solution(String s) {
        boolean answer = true;
        
        answer = s.matches("\\d{4}") || s.matches("\\d{6}");
    
        return answer;
    }
}
```