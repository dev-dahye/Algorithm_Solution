# 프로그래머스 Level1 : 연습문제 두 정수 사이의 합

- [문제](programmers.co.kr/learn/courses/30/lessons/12912)

```java
class Solution {
    public long solution(int a, int b) {
        long answer = 0;
        if(a==b) return a;
        
        if(a>b){
            int temp = a;
            a=b;
            b=temp;
        }
        
        for(int i=a; i<=b; i++){
            answer += i;
        }
                
        return answer;
    }
}
```