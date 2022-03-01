# 프로그래머스 Level1 : Summer/Winter Coding(~2018) 예산

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12982)

```java
import java.util.Arrays;
class Solution {
    public int solution(int[] d, int budget) {
        int answer = 0;
        int useBudget=0;
        Arrays.sort(d);
   
        for(int dep : d){
            useBudget+=dep;
            if(useBudget>=budget){
                if(useBudget==budget){
                    answer++;        
                }
                break;
            }
            answer++;
        }

        return answer;
    }
}
```