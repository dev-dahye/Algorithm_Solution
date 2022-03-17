# 프로그래머스 Level2 : 연습문제 숫자의 표현

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12924)

```java
class Solution {
    public int solution(int n) {
        int answer = 0;
        int sNum = 0;
        int sum = 0;
        
        while(sNum<n){
            sNum++;
            sum = 0;
            int i = 0;
            while(sum<n){
                sum += sNum + i;
                i++;
            }
            if(sum==n) answer++;
        }
        
        return answer;
    }
}
```