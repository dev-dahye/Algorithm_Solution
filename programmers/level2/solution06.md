# 프로그래머스 Level2 : 2017 카카오코드 예선 카카오프렌즈 컬러링북

- [문제](https://programmers.co.kr/learn/courses/30/lessons/1829)

```java
class Solution {
    // 상 하 좌 우
    final int[] dirX = {-1,1,0,0};
    final int[] dirY = {0,0,-1,1};
    // 방문한적 있는지 체크하는 배열
    int[][] checkArr;
    
    //현재 보는 칸(i,j) , return 영역의 크기
    int areaCheck(int i, int j, int m, int n, int[][] picture){
        int currArea = picture[i][j];
        checkArr[i][j] = 1;
        int cnt = 1;
        for(int k=0; k<4; k++){
            //1. 상하좌우 칸이 존재하는가
            int nextX = dirX[k]+i;
            int nextY = dirY[k]+j;
            if(nextX>=0&&nextX<m &&nextY>=0&&nextY< n){
                //2. 같은 영역인가
                //3. 방문한적 있는가
                if(checkArr[nextX][nextY]==0 && picture[nextX][nextY]==currArea)
                    cnt+=areaCheck(nextX,nextY,m,n,picture);
            }
        }
        //System.out.println(i+","+j);
        return cnt;
    }
    
    public int[] solution(int m, int n, int[][] picture) {
        int numberOfArea = 0;
        int maxSizeOfOneArea = 0;
        checkArr = new int[m][n];
    

        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(picture[i][j]!=0 && checkArr[i][j]!=1){
                    int cnt = areaCheck(i,j,m,n,picture);
                    numberOfArea++;
                    maxSizeOfOneArea = maxSizeOfOneArea>cnt? maxSizeOfOneArea:cnt;
                }
            }
        }
        
        int[] answer = new int[2];
        answer[0] = numberOfArea;
        answer[1] = maxSizeOfOneArea;
        return answer;
    }
}
```