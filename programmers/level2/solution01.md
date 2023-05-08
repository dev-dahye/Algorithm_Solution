# 프로그래머스 Level2 : 찾아라 프로그래밍 마에스터 게임 맵 최단거리

- [문제](https://programmers.co.kr/learn/courses/30/lessons/1844?language=java)

```java
import java.util.Queue;
import java.util.LinkedList;

class Solution {
    
    class User{
        int x; 
        int y;
        int cost;
        
        public User(int x, int y, int cost){
            this.x = x;
            this.y = y;
            this.cost = cost;
        }
    }
    
    // 상(0)우(1)하(2)좌(3)
    int[] dirX = {0,1,0,-1}; 
    int[] dirY = {-1,0,1,0};
    
    public int solution(int[][] maps) { 
        int answer = -1;
        Queue<User> q = new LinkedList<>();
        
        int n = maps.length;
        int m = maps[0].length;
        int[][] costMap = new int[n][m];
       
        q.offer(new User(0,0,1));
        costMap[0][0] = 1;
        
        while(!q.isEmpty()){
            User u = q.poll();
            for(int i=0; i<4; i++){
                int nextX = u.x+dirX[i];
                int nextY = u.y+dirY[i];
                int nextCost = u.cost+1;
                
                // index 검사
                if(nextX<0 || nextX>=m){
                    continue;
                }                 
                if(nextY<0 || nextY>=n){
                    continue;
                } 
                
                // 벽검사
                if(maps[nextY][nextX]==0){
                    continue;
                }
                
                // 최소 비용 검사
                if(costMap[nextY][nextX]!=0 && costMap[nextY][nextX] <= nextCost){
                    continue;
                }
                costMap[nextY][nextX] = nextCost;    
       
                // 도착 검사
                if(nextX==m-1 && nextY==n-1){
                    continue;
                }       
                
                q.offer(new User(nextX,nextY,nextCost));
            }
        }
        
        if(costMap[n-1][m-1]!=0){
            answer = costMap[n-1][m-1];
        }
   
        return answer;
    }
}
```
## 
```java
import java.util.*;
class Solution {
    class Position{
        int x,y;
        
        Position(int x, int y){
            this.x = x;
            this.y = y;
        }
        boolean isValid(int width, int height){
            if(x<0 || x>=width) return false;
            if(y<0 || y>=height) return false;
            return true;
        }
    }
    
    public int solution(int[][] maps) { 
        //BFS : Queue
        int mapHeight = maps.length;
        int mapWidth = maps[0].length;

        Queue<Position> queue = new LinkedList<>();
        int[][] count = new int[mapHeight][mapWidth];   // 걸음수를 세는 배열
        boolean[][] visited = new boolean[mapHeight][mapWidth]; // 방문체크 배열

        //초기값
        queue.offer(new Position(0,0)); 
        count[0][0] = 1;
        visited[0][0] = true;

        while(!queue.isEmpty()){
            Position current = queue.poll();
            
            int currentCount = count[current.y][current.x];

            //4가지 경우
            final int[][] moving = {{0,-1},{0,1},{-1,0},{1,0}}; // 좌우상하
            for(int i=0; i<moving.length; i++){
                Position moved = new Position(current.x + moving[i][0], current.y+moving[i][1]);
                if(!moved.isValid(mapWidth,mapHeight)) continue;
                if(visited[moved.y][moved.x]) continue;
                if(maps[moved.y][moved.x] == 0) continue; // 0: 벽, 1: 길

                count[moved.y][moved.x] = currentCount + 1;
                visited[moved.y][moved.x] = true;
                queue.offer(moved);
            }
        }
        int answer = count[mapHeight-1][mapWidth-1];
        if(answer==0) return -1;

        return answer;
    }
}
```