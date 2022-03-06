# 프로그래머스 Level2 : 2021 Dev-Matching: 웹 백엔드 개발자(상반기) 행렬 테두리 회전하기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/77485#)

```java
import java.util.Queue;
import java.util.LinkedList;
import java.util.ArrayList;
class Solution {
    // 우하좌상
    int[] dirR = {0,1,0,-1};
    int[] dirC = {1,0,-1,0};
    ArrayList<Integer> minNumList = new ArrayList<>();
    
    // 회전 시키기 & 최솟값 찾기
    void rotate(int[][] matrix,int rowSize, int columnSize, int[] query){
        Queue<Integer> tempNum = new LinkedList<>();
        int currR = query[0]-1, currC = query[1]-1; 
        
        int min = matrix[currR][currC];
        tempNum.offer(min);
        
        int move = (rowSize)*2 + (columnSize)*2;
        
        int d = 0, rCnt=0, cCnt=0;    //방향
        int num = 0;
        for(int m=0; m<move; m++){
            num = matrix[currR+dirR[d]][currC+dirC[d]];
            min = min>num? num : min;
            
            tempNum.offer(num);
            matrix[currR+dirR[d]][currC+dirC[d]] = tempNum.poll();
            
            currR += dirR[d];
            currC += dirC[d];
            
            if(d==0 || d==2) cCnt++;
            if(d==1 || d==3) rCnt++;
            
            if(rCnt==rowSize){
                d++;
                rCnt=0;
            }
            if(cCnt==columnSize){
                d++;
                cCnt=0;
            }       
        }    
        minNumList.add(min);
    }
        
    
    public int[] solution(int rows, int columns, int[][] queries) {
        int[] answer = new int[queries.length];
        int[][] matrix = new int[rows][columns];
        
        // 행렬 만들기
        int num =1;
        for(int i=0; i<rows; i++){
            for(int j=0; j<columns; j++){
                matrix[i][j] = num++;
            }
        }
        
        // 회전
        for(int[] q : queries){
            rotate(matrix,q[2]-q[0],q[3]-q[1],q);        
        }
        
        for(int i=0; i<minNumList.size(); i++){
            answer[i] = minNumList.get(i);
        }
        return answer;
    }
}
```