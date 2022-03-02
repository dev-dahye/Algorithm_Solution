# 프로그래머스 Level1 : 연습문제 정수 제곱근 판별

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12934)

```java
class Solution {
    public long solution(long n) {
        long answer = 0;
        if(Math.sqrt(n)%1 == 0) return (long)Math.pow(Math.sqrt(n)+1,2);
        else return -1;
    }
}
```