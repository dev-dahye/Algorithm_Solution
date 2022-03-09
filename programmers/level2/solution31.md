# 프로그래머스 Level2 : Summer/Winter Coding(~2018) 배달

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12978)

```java
import java.util.Arrays;
import java.util.ArrayList;
import java.util.PriorityQueue;

class Solution {
    class Node implements Comparable<Node>{
        int num;
        int cost;
        
        public Node(int num, int cost){
            this.num = num;
            this.cost = cost;
        }
        
        @Override
        public int compareTo(Node node){ //cost가 작은쪽을 우선순위
            return this.cost < node.cost? -1 : 1;
        }
        
    }
    public int solution(int N, int[][] road, int K) {
        int answer = 0;
        
        int[] costArr = new int[N+1];
        Arrays.fill(costArr,Integer.MAX_VALUE);
        
        // 연결된 노드 리스트
        ArrayList<Node>[] adjList = new ArrayList[N+1];
        for(int i=1; i<=N; i++){
            adjList[i] = new ArrayList<>();
        }
        
        // 연결된 노드 셋팅
        for(int i=0; i<road.length; i++){
            int form = road[i][0];
            int to = road[i][1];
            int cost = road[i][2];
            
            adjList[form].add(new Node(to,cost));
            adjList[to].add(new Node(form,cost));
        }
        
        // 코스트가 작은 것부터 탐색하기 위해 PriorityQueue
        PriorityQueue<Node> pQue = new PriorityQueue<>();
        
        //시작노드
        int start = 1;
        costArr[start] = 0;
        pQue.add(new Node(1,0));
        
        // 다익스트라 알고리즘으로 시작노드부터 각 노드 최소비용 갱신
        while(!pQue.isEmpty()){
            Node node = pQue.poll();
            int currNum = node.num;
            int currCost = node.cost;
            
            //최소비용이 아니면 continue
            if(costArr[currNum]<currCost) continue;
            
            for(int i=0; i<adjList[currNum].size(); i++){
                // 다음노드 정보
                int nextNum = adjList[currNum].get(i).num;
                int nextCost = adjList[currNum].get(i).cost + currCost;
                
                //최소비용 계산
                if(costArr[nextNum] > nextCost){
                    costArr[nextNum] = nextCost;
                    pQue.add(new Node(nextNum,nextCost));
                }
            }
        }

        for(int i=1; i<=N; i++){
            if(costArr[i]<=K) answer++;
        }
        return answer;
    }
}
```
<br>
<br>

- - -

## Reference
- <https://github.com/jki503/CS_for-tech-interview/tree/main/algorithm#%EB%8B%A4%EC%9D%B5%EC%8A%A4%ED%8A%B8%EB%9D%BCdijkstra-%EC%8B%9C%EA%B0%84-%EB%B3%B5%EC%9E%A1%EB%8F%84>
- 