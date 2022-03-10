# 프로그래머스 Level2 : 2018 KAKAO BLIND RECRUITMENT [1차] 프렌즈4블록

- [문제](https://programmers.co.kr/learn/courses/30/lessons/17679)

```java
class Solution {
    public int solution(int m, int n, String[] board) {
        int answer = -1;
        char[][] b = new char[m][n];
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                b[i][j] = board[i].charAt(j);
            }
        }
        
        int cnt = 0;
        while(answer!=cnt){
            answer=cnt;
            boolean[][] isPop = new boolean[m][n];
            for(int i=0; i<m-1; i++){
                for(int j=0; j<n-1; j++){
                    char currBlock = b[i][j];
                    if(currBlock=='X') continue;

                    // currBlock=왼쪽위 터트릴수 있는 블록 체크
                    char rBlock = b[i][j+1];
                    char bBlock = b[i+1][j];
                    char rbBlock = b[i+1][j+1];

                    if(currBlock==rBlock&&currBlock==bBlock&&currBlock==rbBlock){
                        isPop[i][j] = true;
                        isPop[i][j+1] = true;
                        isPop[i+1][j] = true;
                        isPop[i+1][j+1] = true;
                    }
                }
            }
            for(int i=0; i<m; i++){
                for(int j=0; j<n; j++){
                    if(isPop[i][j]){
                        cnt++;
                        b[i][j] = 'X';
                    }
                }
            }

            for(int i=m-1; i>0; i--){
                for(int j=0; j<n; j++){
                    if(b[i][j]=='X'){
                        int k = i-1;
                        for(; k>=0; k--){
                            if(b[k][j]!='X') break;
                        }
                        if(k>=0){
                            b[i][j] = b[k][j];
                            b[k][j] = 'X';       
                        }
                    }
                }
            }
        }        
        return answer;
    }
}
```