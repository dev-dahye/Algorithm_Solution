# 프로그래머스 Level1 : 월간 코드 챌린지 시즌1 내적

- [문제](https://programmers.co.kr/learn/courses/30/lessons/70128)

```java
class Solution {
    public int solution(int[] a, int[] b) {
        int answer = 0;
        int l = a.length;
        
        for(int i=0; i<l; i++){
            answer += a[i]*b[i];
        }
        return answer;
    }
}
```