# 프로그래머스 Level1 : 연습문제 약수의 합

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12928)

```java
class Solution {
    public int solution(int n) {
        int answer = 0;
        for(int i=1; i<=Math.sqrt(n); i++){
            if(n%i == 0){
                answer += i;
                answer += n/i;
            }
            
            if(i==Math.sqrt(n)){
                answer-= i;
            }
        }
        return answer;
    }
}
```