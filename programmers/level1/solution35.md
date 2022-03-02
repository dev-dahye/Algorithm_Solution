# 프로그래머스 Level1 : 연습문제 소수 찾기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12921)

```java
class Solution {
    public int solution(int n) {
        int answer = 0;
        boolean isPrime = true;
        
        for(int j=2; j<=n; j++ ){
            for(int i=2; i<=Math.sqrt(n); i++ ){
                if(i!=j && j%i==0){
                    isPrime = false;
                    break;
                }
                isPrime = true;
            }
            if(isPrime){
                answer++;       
                isPrime = false;
            }
        }
        return answer;
    }
}
```