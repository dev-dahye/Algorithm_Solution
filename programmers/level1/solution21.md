# 프로그래머스 Level1 : 위클리 챌린지 최소직사각형

- [문제](https://programmers.co.kr/learn/courses/30/lessons/86491)

```java
class Solution {
    public int solution(int[][] sizes) {
        int answer = 0;
        int s = sizes.length;
        int maxV = 0;
        int maxH = 0;
        int temp = 0;
        
        for(int i=0; i<s; i++){
            if(sizes[i][0]<sizes[i][1]){
                temp = sizes[i][0];
                sizes[i][0] = sizes[i][1];
                sizes[i][1] = temp;
            }
            if(maxH<sizes[i][0]){
                maxH = sizes[i][0];
            }
            if(maxV<sizes[i][1]){
                maxV = sizes[i][1];
            }
        }
        
        answer = maxH*maxV;
        
        return answer;
    }
}
```