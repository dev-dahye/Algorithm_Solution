# 프로그래머스 Level2 : 연습문제 가장 큰 정사각형 찾기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12905)

```java
class Solution{
    public int solution(int[][] board){
        int answer = 1;
        int rows = board.length;
        int cols = board[0].length;
        boolean isAllZero = true;
        
        if(board[0][0]==1) isAllZero = false;
        for (int i = 1; i < rows; i++) {
            for (int j = 1; j < cols; j++) {
                if(board[i][j] == 0) continue;
                isAllZero = false;
                board[i][j] = Math.min(Math.min(board[i-1][j], board[i][j-1]), board[i-1][j-1])+1;
                answer = Math.max(answer, board[i][j]);
            }
        }

        return isAllZero? 0 : answer*answer;
    }
}
```

## 효율성테스트X
```java
class Solution{
    int findRectSize(int row, int col, int l, int[][] board){
        if(l+row>board.length || l+col>board[0].length) return -1;
        for(int i=0; i<l; i++){
            if(board[row+l-1][col+i]==0) return l-1;
        }
        for(int i=0; i<l; i++){
            if(board[row+i][col+l-1]==0) return l-1;        
        }      
        
        int next = findRectSize(row,col,l+1,board);
        return next==-1? l : next;
    }
    
    boolean isRect(int row, int col, int l, int[][] board){
        if(l+row>board.length || l+col>board[0].length) return false;
        for(int i=0; i<l; i++){
            for(int j=0; j<l; j++){
                if(board[i+row][j+col]==0) return false;
            }
        }
        
        return true;
    }
    
    public int solution(int[][] board){
        int rows = board.length;
        int cols = board[0].length;
        boolean isAllZero = true;
        
        if(rows==1&&cols==1){
            if(board[0][0]==1) return 1;
            else return 0;
        }
        int max = 1;
        
        for(int i=0; i<rows; i++){
            for(int j=0; j<cols; j++){
                if(board[i][j]==1){
                    isAllZero = false;
                    if(max==1)
                        max = Math.max(max,findRectSize(i,j,2,board));
                    else{
                        if(isRect(i,j,max,board)){
                            max = Math.max(max,findRectSize(i,j,max,board));
                        }
                    }
                        
               } 
            }
        }
            
        
        return isAllZero? 0:max*max;
    }
}
```

<br>
<br>

- - -

## Reference
- <https://programmers.co.kr/questions/19991>