# 프로그래머스 Level2 : 연습문제 땅따먹기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12913)

```java
import java.util.Arrays;
class Solution {
    int max(int a, int b, int c){
        int[] arr = {a,b,c};
        Arrays.sort(arr);
        return arr[arr.length-1];
    }
    
    int solution(int[][] land) {
        int answer = 0;
       
        for(int row=1; row<land.length; row++){
            land[row][0] += max(land[row-1][1],land[row-1][2],land[row-1][3]);
            land[row][1] += max(land[row-1][0],land[row-1][2],land[row-1][3]);
            land[row][2] += max(land[row-1][0],land[row-1][1],land[row-1][3]);
            land[row][3] += max(land[row-1][0],land[row-1][1],land[row-1][2]);
        }
      
        answer = Integer.MIN_VALUE;
        for(int i=0; i<4; i++){
            if (land[land.length-1][i] > answer) {         
                answer = land[land.length-1][i];     
            } 
        }
        
        return answer;
    }
}
```