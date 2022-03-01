# 프로그래머스 Level1 : 연습문제 문자열 내 p와 y의 개수

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12916)

```java
class Solution {
    boolean solution(String s) {
        boolean answer = true;
        int p = 0;
        int y = 0;

        for(char c : s.toCharArray()){
            if(c=='p' || c=='P') p++;
            else if(c=='y' || c=='Y') y++;
        }
        
        answer = (p==y);
        return answer;
    }
}
```