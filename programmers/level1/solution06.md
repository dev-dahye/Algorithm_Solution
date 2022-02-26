# 프로그래머스 Level1 : 월간 코드 챌린지 시즌2 음양 더하기


- [문제](https://programmers.co.kr/learn/courses/30/lessons/76501?language=java)

```java
class Solution {
    public int solution(int[] absolutes, boolean[] signs) {
        int answer = 0;
        for(int i=0; i<signs.length; i++){
            answer += signs[i]? absolutes[i] : (-1)*absolutes[i];
        }
        
        return answer;
    }
}
```