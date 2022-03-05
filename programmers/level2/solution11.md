# 프로그래머스 Level2 : 힙(Heap) 더 맵게

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42626)

```java
import java.util.PriorityQueue;

class Solution {    
    public int solution(int[] scoville, int K) {
        PriorityQueue<Integer> minHeap = new PriorityQueue<Integer>(); 
        int answer = 0;
        int foodCnt = scoville.length;
        
        for(int s : scoville){
            minHeap.add(s);
        }

        while(foodCnt>1){
            // 모든 음식의 스코빌지수가 K이상일때 종료
            for(int s : minHeap){
                if(s<K){
                    break;
                }       
                return answer;
            }
            
            int min1 = minHeap.poll();
            int min2 = minHeap.poll();
            minHeap.add(min1+min2*2);
            
            foodCnt--;
            answer++;
        }

        // 모든 음식을 섞었는데도 K미만이면 return -1
        return minHeap.peek()<K? -1 : answer;
    }
}
```

<br>
<br>

- - -
## Reference
-<http://oniondev.egloos.com/288232>