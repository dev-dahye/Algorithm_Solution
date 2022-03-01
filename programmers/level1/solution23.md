# 프로그래머스 Level1 : 위클리 챌린지 부족한 금액 계산하기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/82612)

```java
class Solution {
    public long solution(int price, int money, int count) {
        long answer = -1;
        long pay = 0;
        
        for(int i=1; i<=count; i++){
            pay += price*i;
        }

        if(money-pay<0)
            answer = pay - money;
        else 
            answer = 0;
        
        return answer;
    }
}
```