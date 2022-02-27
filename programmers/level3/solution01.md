# 프로그래머스 Level3 : 깊이/너비 우선 탐색(DFS/BFS) 네트워크

- [문제](https://programmers.co.kr/learn/courses/30/lessons/43162?language=java)

```java
class Solution {
    // 체크할 컴퓨터, 컴퓨터와 연결된 컴퓨터들, 총 컴퓨터 갯수, 방문 체크 배열 
    void visit(int computer, int[][] computers, int n, boolean[] visited){
        visited[computer] = true;
        int[] network = computers[computer];
        
        for(int i=0; i<n; i++){
            if(network[i] == 1){
                if(visited[i]==false){
                    visit(i, computers, n, visited);    
                }    
            }
        }
    }
    
    public int solution(int n, int[][] computers) {
        int answer = 0;    
        boolean[] visited = new boolean[n];
        int currCom = 0;
        
        // 루트 컴퓨터 체크 
        visit(0, computers, n, visited);    
        answer++;
        
        // 컴퓨터와 연결된 다른 컴퓨터들 모두 확인
        for(int i=1; i<n; i++){
            if(!visited[i]){
                visit(i, computers, n, visited);
                answer++;
            }
        }
        
        return answer;
    }
}
```