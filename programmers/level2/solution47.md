# 프로그래머스 Level2 : 월간 코드 챌린지 시즌1 이진 변환 반복하기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/70129)

```java
class Solution {
    public int[] solution(String s) {
        int cnt = 0;
        int zeroCnt = 0;
        
        while(!s.equals("1")){
            cnt++;
            int lenBefore = s.length();
            s = s.replace("0","");
            int lenAfter = s.length();
            
            zeroCnt += (lenBefore-lenAfter);
            s = Integer.toBinaryString(lenAfter);
        }
        
       int[] answer = {cnt,zeroCnt};
        
        return answer;
    }
}
```