# 프로그래머스 Level1 : 연습문제 자릿수 더하기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12931)

```java
public class Solution {
    public int solution(int n) {
        int answer = 0;
        
        while(n!=0){
            answer += n%10;    
            n/=10;
        }

        return answer;
    }
}
```