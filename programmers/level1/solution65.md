# 프로그래머스 Level1 : 과일 장수

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/135808)

```java
import java.util.PriorityQueue;
import java.util.Collections;
class Solution {
    public int solution(int k, int m, int[] score) {
        PriorityQueue<Integer> appleQueue = new PriorityQueue<>(Collections.reverseOrder());
        int answer = 0;
        for(int p: score){
            appleQueue.offer(p);
        }
        while(appleQueue.size()>=m){
            int p = k;
            for(int i=0; i<m; i++){
                p = Math.min(p,appleQueue.poll());
            }
            answer+=p*m;
        }
        return answer;
    }
}
```

```java
import java.util.Arrays;
class Solution {
    public int solution(int k, int m, int[] score) {
        Arrays.sort(score);
        int answer = 0;
        for(int i=score.length; i>=m; i-=m){
            answer += score[i-m]*m;
        }
        return answer;
    }
}
```