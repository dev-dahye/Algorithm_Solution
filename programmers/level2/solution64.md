# 프로그래머스 Level2 : 연습문제 연습문제 최솟값 만들기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12941)

```java
import java.util.Arrays;
class Solution{
    public int solution(int []A, int []B){
        int answer = 0;
        Arrays.sort(A);
        Arrays.sort(B);
        
        for(int i=0; i<A.length; i++){
            answer += A[i]*B[B.length-1-i];
        }

        return answer;
    }
}
```