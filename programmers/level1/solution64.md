# 프로그래머스 Level1 : 명예의 전당 (1)

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/138477)

## ArrayList
```java
import java.util.ArrayList;
import java.util.Collections;
class Solution {
    public int[] solution(int k, int[] score) {
        int[] answer = new int[score.length];
        ArrayList<Integer> hall = new ArrayList<Integer>();
        for(int i=0; i<score.length; i++){
            hall.add(score[i]);
            Collections.sort(hall);
            Collections.reverse(hall);
            if(i>=k){
                hall = new ArrayList(hall.subList(0,k));    
            }
            answer[i] = hall.get(hall.size()-1);
        }
        return answer;
    }
}
```
## PriorityQueue
```java
import java.util.PriorityQueue;
import java.util.Collections;
class Solution {
    public int[] solution(int k, int[] score) {
        int[] answer = new int[score.length];
        PriorityQueue<Integer> hall = new PriorityQueue<>();
        for(int i=0; i<score.length; i++){
            hall.offer(score[i]);
            if(hall.size()>k){
                hall.poll();
            }
            answer[i] = hall.peek();
        }
        return answer;
    }
}
```

## ArrayList / PriorityQueue 연산시간 차이
|테스트|ArrayList|PriorityQueue|
|---|---|---|
|테스트 1 〉  |통과 (0.58ms, 81.8MB)   |통과 (0.30ms, 84.5MB) |
|테스트 2 〉  |통과 (0.30ms, 81.5MB)   |통과 (0.33ms, 76.3MB) |
|테스트 3 〉  |통과 (0.42ms, 77.8MB)   |통과 (0.31ms, 71.9MB) |
|테스트 4 〉  |통과 (0.35ms, 76.8MB)   |통과 (0.46ms, 71.9MB) |
|테스트 5 〉  |통과 (0.35ms, 73MB)     |통과 (0.35ms, 76.8MB) |
|테스트 6 〉  |통과 (0.37ms, 77.7MB)   |통과 (0.50ms, 79.6MB) |
|테스트 7 〉  |통과 (0.80ms, 74.7MB)   |통과 (0.50ms, 76.4MB) |
|테스트 8 〉  |통과 (0.68ms, 77.7MB)   |통과 (0.36ms, 77.9MB) |
|테스트 9 〉  |통과 (0.68ms, 77.7MB)   |통과 (0.47ms, 87.9MB) |
|테스트 10〉  |통과 (0.79ms, 75.9MB)   |통과 (0.36ms, 70.2MB) |
|테스트 11〉  |통과 (1.18ms, 76.3MB)   |통과 (0.56ms, 67.4MB) |
|테스트 12〉  |통과 (10.06ms, 95MB)    |통과 (1.67ms, 78.7MB) |
|테스트 13〉  |통과 (9.41ms, 79.1MB)   |통과 (1.27ms, 72.6MB) |
|테스트 14〉  |통과 (11.02ms, 79.1MB)  |통과 (1.61ms, 78.3MB) |
|테스트 15〉  |통과 (23.38ms, 88.5MB)  |통과 (2.12ms, 82.1MB) |
|테스트 16〉  |통과 (20.14ms, 78.8MB)  |통과 (2.02ms, 75.5MB) |
|테스트 17〉  |통과 (24.28ms, 86.4MB)  |통과 (2.08ms, 71.5MB) |
|테스트 18〉  |통과 (16.05ms, 80.7MB)  |통과 (1.84ms, 72.3MB) |
|테스트 19〉  |통과 (3.18ms, 67.7MB)   |통과 (1.50ms, 78.3MB) |
|테스트 20〉  |통과 (2.99ms, 81.8MB)   |통과 (3.46ms, 77.3MB) |
|테스트 21〉  |통과 (4.69ms, 81.2MB)   |통과 (1.94ms, 78.8MB) |
|테스트 22〉  |통과 (5.28ms, 75.1MB)   |통과 (2.46ms, 80.6MB) |
|테스트 23〉  |통과 (4.37ms, 77.1MB)   |통과 (1.75ms, 80.8MB) |
|테스트 24〉  |통과 (4.12ms, 68.9MB)   |통과 (1.39ms, 74.7MB) |
|테스트 25〉  |통과 (4.02ms, 76MB)     |통과 (1.66ms, 72.5MB) |
|테스트 26〉  |통과 (0.28ms, 72.9MB)   |통과 (0.43ms, 88.4MB) |

<br>
<br>

- - -