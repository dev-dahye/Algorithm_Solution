# 프로그래머스 Level2 : 연습문제 행렬의 곱셈

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12949)

```java
class Solution {
    public int[][] solution(int[][] arr1, int[][] arr2) {
        int row = arr1.length;
        int col = arr2[0].length;
        int[][] answer = new int[row][col];
        
        int n = 0;
        int r = 0;
        int c = 0;
        while(n<row*col){
            for(int i=0; i<arr2.length; i++){
                answer[r][c] += arr1[r][i] * arr2[i][c];   
            }
            c = (c+1)%col;
            n++;
            if(n%col==0) r++;
        }
        
        return answer;
    }
}
```

