# 프로그래머스 Level2 : 탐욕법(Greedy) 구명보트

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42885)

```java
import java.util.Deque;
import java.util.LinkedList;
import java.util.Arrays;
class Solution {
    public int solution(int[] people, int limit) {
        int answer = 0;
        Arrays.sort(people);
        Deque<Integer> dQue = new LinkedList<>();
        for(int p : people){
            dQue.add(p);
        }
        
        
        while(!dQue.isEmpty()){
            int p = dQue.pollLast();
            if(!dQue.isEmpty() && p+dQue.getFirst() <= limit){
                dQue.pollFirst();
            }
            answer++;
        }
        
        return answer;
    }
}
```