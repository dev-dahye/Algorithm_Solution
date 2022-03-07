# 프로그래머스 Level2 : 월간 코드 챌린지 시즌3 빛의 경로 사이클

- [문제](https://programmers.co.kr/learn/courses/30/lessons/86052)

## 클래스 선언
```java
import java.util.ArrayList;
import java.util.Collections;
class Solution {
    //상우하좌
    int[] dirR = {-1,0,1,0};
    int[] dirC = {0,1,0,-1};
    int cnt=0;
    int rows, cols;
    
    int findCycle(int r, int c, int lightDir, Node[][] grids){
        cnt = 0;
        Node currNode = grids[r][c];
        while(true){
            lightDir = currNode.comeIn(lightDir);
            if(lightDir==-1){
                return cnt;
            } else{
                r=(r+dirR[lightDir]+rows)%rows;
                c=(c+dirC[lightDir]+cols)%cols;
                currNode = grids[r][c];   
            }
        }
    }
    
    class Node{
        boolean isVisited;
        char lens;    // S R L 
        boolean[] isComeIn = new boolean[4]; // 이 렌즈에 해당 빛의 방향이 들어오는지, 
        int lightDir;
        
        Node(char lens){
            this.lens = lens;
        }
                
        int refraction(){
            if(this.lens=='S') return this.lightDir;
            else if(this.lens=='R'){
                return (this.lightDir+1)%4;
            } else{
                return (this.lightDir+3)%4;
            }
        }
        
        int comeIn(int ld){
            if(!isComeIn[ld]){
                cnt++;
                isComeIn[ld] = true;
                this.lightDir = ld;
                return this.refraction();
            } else {
                return -1;
            }
        }
    }
    
    public int[] solution(String[] grid) {
        ArrayList<Integer> cntList = new ArrayList<>();
        
        rows = grid.length;
        cols = grid[0].length();
        
        Node[][] grids = new Node[rows][cols];
        for(int r=0; r<rows; r++){
            for(int c=0; c<cols; c++){
                grids[r][c] = new Node(grid[r].charAt(c));
            }
        }
        
         for(int r=0; r<rows; r++){
            for(int c=0; c<cols; c++){
                for(int d=0; d<4; d++){
                    if(grids[r][c].isComeIn[d])
                        continue;
                    cntList.add(findCycle(r, c, d, grids));
                }
            }
        }
        
        
        int[] answer = new int[cntList.size()];
        Collections.sort(cntList);
        for(int i=0; i<cntList.size(); i++){
            answer[i] = cntList.get(i);
        }
        
        return answer;
    }
}
```

### 삼차배열 사용
```java
import java.util.ArrayList;
import java.util.Collections;
class Solution {
    //상우하좌
    int[] dirR = {-1,0,1,0};
    int[] dirC = {0,1,0,-1};
    int rows, cols;    
    boolean[][][] isVisited;
    
    //r,c,d,grid
    int findMoreCycle(int r, int c, int ld, String[] grid){
        int cnt = 0;
        while(true){
            if(isVisited[r][c][ld])
                break;
            
            cnt++;
            isVisited[r][c][ld] = true;
            
            if(grid[r].charAt(c)=='R'){
                ld = (ld+1)%4;
            } else if(grid[r].charAt(c)=='L'){
                ld = (ld+3)%4;
            }
            
            r=(r+dirR[ld]+rows)%rows;
            c=(c+dirC[ld]+cols)%cols;
        }
        
        return cnt;
    }
    
    public int[] solution(String[] grid) {
        ArrayList<Integer> cntList = new ArrayList<>();
        rows = grid.length;
        cols = grid[0].length();
        isVisited = new boolean[rows][cols][4];
        
         for(int r=0; r<rows ; r++){
            for(int c=0; c<cols; c++){
                for(int d=0; d<4; d++){
                    if(isVisited[r][c][d]){
                        continue;
                    }
                    cntList.add(findMoreCycle(r,c,d,grid));
                }
            }
         }
        
        int[] answer = new int[cntList.size()];
        Collections.sort(cntList);
        for(int i=0; i<cntList.size(); i++){
            answer[i] = cntList.get(i);
        }
        
        return answer;
    }
}
```


<br>
<br>

- - -

## Reference
-<https://github.com/jki503/Algorithm_Solution/blob/main/programmers/level2/solution56.md>