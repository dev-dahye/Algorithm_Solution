# 프로그래머스 Level1 : 공원 산책

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/172928)

```java
class Solution {
    public int[] solution(String[] park, String[] routes) {
        //N, S, W, E
        int[] dirX = {-1,1,0,0}; //H
        int[] dirY = {0,0,-1,1}; //W
        
        int W = park[0].length();
        int H = park.length;  
        
        int dogX = 0;
        int dogY = 0;
        
        //시작지점 찾기
        findStart:
        for(int x=0; x<H; x++){
            for(int y=0; y<W; y++){
                if(park[x].charAt(y)=='S'){
                    dogX = x;
                    dogY = y;
                    break findStart;
                }
            }
        }
    
        // 산책 명령 확인
        for(String r : routes){
            String opString = r.split(" ")[0];
            int op = 0;
            int n = Integer.parseInt(r.split(" ")[1]);
            
            switch(opString){
                case "N":
                    op = 0;
                    break;
                case "S":
                    op = 1;
                    break;
                case "W":
                    op = 2;
                    break;
                case "E":
                    op = 3;
                    break;   
            }
            
            //공원을 벗어나는지 확인
            int checkX = dogX+(n*dirX[op]);
            int checkY = dogY+(n*dirY[op]);
            if(checkX>=H || checkX<0 || checkY>=W || checkY<0) {
                continue;
            }
                
               
            //장애물을 만나는지 확인
            boolean flag = false;
            checkX = dogX;
            checkY = dogY;
            for(int i=0; i<n; i++){
                checkX += dirX[op];
                checkY += dirY[op];
                
                if(park[checkX].charAt(checkY)=='X'){
                    flag=true;
                    break;
                }
            }
            if(flag){
                continue;
            }
            
            dogX += n*dirX[op];
            dogY += n*dirY[op];
        }
        
        int[] answer = {dogX,dogY};
        
        return answer;
    }
}
```