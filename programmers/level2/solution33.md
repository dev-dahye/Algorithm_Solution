# 프로그래머스 Level2 : 스택/큐 다리를 지나는 트럭

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42583)

```java
import java.util.Queue;
import java.util.LinkedList;
import java.util.HashMap;
import java.util.Map;

class Solution {
    class Truck{
        int weight;
        int loc;
        
        public Truck(int weight, int loc){
            this.weight = weight;
            this.loc = loc;
        }
    }
    
    public int solution(int bridge_length, int weight, int[] truck_weights) {
        int answer = 0;
        int currWeight = 0;
        Queue<Integer> waitTruck = new LinkedList<>();
        Queue<Truck> onBridgeTruck = new LinkedList<>();
        
        for(int t : truck_weights){
            waitTruck.offer(t);
        }
        
        int scd = 1;
        int w = waitTruck.poll();
        onBridgeTruck.offer(new Truck(w,1));
        currWeight += w;

        while(!(waitTruck.isEmpty()&&onBridgeTruck.isEmpty())){
            scd++;
            
            // 다리위의 트럭들 1씩 전진
            if(!onBridgeTruck.isEmpty()){
                for(Truck truck : onBridgeTruck){
                    truck.loc+=1;
                }
                if(onBridgeTruck.peek().loc>bridge_length){
                    currWeight -= onBridgeTruck.poll().weight;
                }
            }
            
            // 다리에 올라갈수 있는 무게면 진입
            if(!waitTruck.isEmpty()&&currWeight+waitTruck.peek()<=weight){
                int t = waitTruck.poll();
                onBridgeTruck.offer(new Truck(t, 1));
                currWeight += t;
            }
        }
        
        return scd;
    }
}
```