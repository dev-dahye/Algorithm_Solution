# 프로그래머스 Level1 : 월간 코드 챌린지 시즌3 없는 숫자 더하기


- [문제](https://programmers.co.kr/learn/courses/30/lessons/86051?language=java)

```java
 class Solution {
    public int solution(int[] numbers) {
        int answer = 45;
        
        for(int num:numbers){
            answer -= num;
        }
        return answer;
    }
}
```