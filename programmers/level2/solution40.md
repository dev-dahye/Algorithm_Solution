# 프로그래머스 Level2 : 월간 코드 챌린지 시즌1 삼각 달팽이

- [문제](https://programmers.co.kr/learn/courses/30/lessons/68645#)

```java
class Solution {
    public int[] solution(int n) {
        int[][] numArr = new int[n][];
        int num = 0;
        
        for(int i=1; i<=n; i++) {
            num+=i;
            numArr[i-1] = new int[i];
        }
        
        int col = 0;
        int row = n-1;
        boolean isDown = true;
        for(int i=1, j=0; i<=num; i++){
            if(j<row && isDown){
                numArr[j++][col] = i;
                
            } else if(j==row && isDown){
                for(int k=col; k<=row-col; k++){
                    numArr[j][k] = i++;
                }
                col++;
                j--;
                i--;
                row--;
                isDown = false;
            } else if(j<=row && !isDown){
                numArr[j][numArr[j].length-col] = i;
                if(j<n-row+col){
                    isDown = true;
                    j--;
                    continue;
                }
                j--;
            }
        }
        
        int[] answer = new int[num];
        int index = 0;
        for(int j=0; j<n; j++){
            for(int i : numArr[j]){
                answer[index++] = i;
            }
        }
        
        return answer;
    }
}
```