# 프로그래머스 Level1 : 연습문제 평균 구하기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12944)

```java
class Solution {
    public double solution(int[] arr) {
        double answer = 0;
        for(int num: arr){
            answer+=num;
        }
        answer/=arr.length;
        return answer;
    }
}
```