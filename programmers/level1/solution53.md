# 프로그래머스 Level1 : 연습문제 x만큼 간격이 있는 n개의 숫자

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12954)

```java
class Solution {
    public long[] solution(int x, int n) {
        long[] answer = new long[n];
        
        long i = x;
        for(int j=0; j<n; j++){
            answer[j] = i;
            i+=x;
        }
        return answer;
    }
}
```