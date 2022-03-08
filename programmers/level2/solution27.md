# 프로그래머스 Level2 : 2017 팁스타운 예상 대진표

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12985)

```java
import java.util.Queue;
import java.util.LinkedList;
class Solution{
    public int solution(int n, int a, int b){
        Queue<Integer> player = new LinkedList<>();
        int answer = 1;
        
        for(int i=0; i<n; i++){
            player.offer(i+1);
        }
        while(true){
            for(int i=0; i<player.size(); i++){
                int p1 = player.poll();
                int p2 = player.poll();
                if(p1==a&&p2==b) return answer;
                else if(p1==b&&p2==a) return answer;
                
                if(p1==a||p2==a){
                    player.offer(a);
                } else if(p1==b||p2==b){
                    player.offer(b);
                } else{
                    player.offer(Math.max(p1,p2));
                }
            }
            answer++;
        }
    }
}
```