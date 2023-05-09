# 프로그래머스 Level3 : 정수 삼각형

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/43105)

## 위에서 아래로 내려가면서 
```java
class Solution {
    public int solution(int[][] triangle) {
        int answer = 0;
        for(int i=1; i<triangle.length; i++){
            for(int j=0; j<triangle[i].length; j++){
                
                if(j == 0){
                    triangle[i][j] = triangle[i][j] + triangle[i-1][j];    
                } else if(i==j){
                    triangle[i][j] = triangle[i][j] + triangle[i-1][j-1];    
                } else{
                    int left = triangle[i][j] + triangle[i-1][j-1];
                    int right = triangle[i][j] + triangle[i-1][j];
                    triangle[i][j] = Math.max(left,right);

                }
                
                answer = Math.max(answer, triangle[i][j]);
            }
        }
        return answer;
    }
}
```

## 아래에서 위로 올라가면서
```java
class Solution {
    public int solution(int[][] triangle) {
        for(int i=triangle.length-2; i>=0; i--){
            for(int j=0; j<triangle[i].length; j++){
                int left = triangle[i][j] + triangle[i+1][j];
                int right = triangle[i][j] + triangle[i+1][j+1];
                triangle[i][j] = Math.max(left,right);

            }
        }
        return triangle[0][0];
    }
}
```

<details>
<summary><b>배열추가..</b></summary>
<div markdown="1">

```java
class Solution {
    public int solution(int[][] triangle) {
        int[][] sumTriangle = new int[triangle.length][];
        for(int i=0; i<triangle.length; i++){
            sumTriangle[i] = new int[i+1];
        }
        sumTriangle[0][0] = triangle[0][0];
        for(int i=1; i<triangle.length; i++){
            for(int j=0; j<triangle[i].length; j++){
                if(j==0){
                    sumTriangle[i][j] = sumTriangle[i-1][j]+triangle[i][j];
                }else if(j==triangle[i].length-1){
                    sumTriangle[i][j] = sumTriangle[i-1][j-1]+triangle[i][j];
                }else{
                    sumTriangle[i][j] = Math.max(sumTriangle[i-1][j-1]+triangle[i][j],sumTriangle[i-1][j]+triangle[i][j]);
                }
            }
        }
        int answer = 0;
        for(int i : sumTriangle[triangle.length-1]){    
            answer = Math.max(answer,i);
        }
        
        return answer;
    }
}
```

</div>
</details> 
