# 프로그래머스 Level3 : 숫자게임

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/12987)

```java
import java.util.*;
class Solution {
    public int solution(int[] A, int[] B) {
        int answer = 0;
        Arrays.sort(A);
        Arrays.sort(B);
        for(int i=0, j=0; i<A.length && j<B.length;){
            if(A[i]>=B[j]){
                j++;                
            } else if(A[i]<B[j]){
                answer++;
                i++;
                j++;               
            }
        }
        
        return answer;
    }
}
```

## 시뮬레이션 
시간 초과
```java
import java.util.*;
class Solution {
    public int solution(int[] A, int[] B) {
        Arrays.sort(A);
        Arrays.sort(B);
        int index = B.length - 1;
        int answer = 0;
        for(int i=A.length-1; i>=0; i--){
            if(A[i] < B[index]){
                index--;
                answer++;
            }
        }
        
        return answer;
    }
}
```