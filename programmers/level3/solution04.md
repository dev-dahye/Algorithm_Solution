# 프로그래머스 Level3 : 이분탐색 입국심사

- [문제](https://programmers.co.kr/learn/courses/30/lessons/43238)

```java
import java.util.Arrays;

class Solution {
    public long solution(int n, int[] times) {
        long answer = 0;
        Arrays.sort(times);
        long start = 0;
        long end = (long)times[times.length-1]*n; // 가장 오래걸리는 경우
        
        while(start <= end) {
            long mid = (end + start) / 2;
            long finish = 0;    // 심사가 끝난 사람의 수
            for(int time : times) {
                if(time > mid)
                    break;
                finish += mid / time; // mid시간 동안 해당 심사관이 처리할수 있는 사람의 수
            }

            if(finish >= n) {
                end = mid-1;
                answer = mid;
            }
            else if( finish < n) {
                start = mid+1;
            }

        }
        
        return answer;
    }
}
```