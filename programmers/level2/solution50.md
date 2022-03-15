# 프로그래머스 Level2 : 월간 코드 챌린지 시즌1 쿼드압축 후 개수 세기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/68936)

```java
import java.util.ArrayList;
class Solution {
    ArrayList<Integer[]> numArr = new ArrayList<>();
    
    void zip(int n, int[][] arr){
        if(n==1) return;
        else{
            int num = arr[0][0];
            boolean isZip = true;
            for(int i=0; i<n; i++){
                for(int j=0; j<n; j++){
                    if(arr[i][j]!=num){
                        isZip = false;
                        break;
                    }
                }
                if(!isZip) break;
            }
            
            if(isZip){
                Integer[] zipNum = {num,n*n-1};
                numArr.add(zipNum);
            } else{
                int m = n/2;
                int[][] arr1 = new int[m][m];
                int[] row = {0,0,m,m};
                int[] col = {0,m,0,m};
                
                for(int d=0; d<4; d++){
                    for(int i=0+row[d]; i<m+row[d]; i++){
                        for(int j=0+col[d]; j<m+col[d]; j++){
                            arr1[i-row[d]][j-col[d]] = arr[i][j];
                        }
                    }
                    zip(m,arr1);
                }
            }
        }
    }

    public int[] solution(int[][] arr) {
        zip(arr.length,arr);
        int zeroCnt = 0;
        int oneCnt = 0;
        
        for(int i=0;i<arr.length; i++){
            for(int j=0;j<arr.length; j++){
                if(arr[i][j]==1) oneCnt++;
                else zeroCnt++;
            }
        }
        
        for(Integer[] a : numArr){
            if(a[0]==1) oneCnt -= a[1];
            else zeroCnt -= a[1];
        }
        
        int[] answer = {zeroCnt, oneCnt};
        return answer;
    }
}
```