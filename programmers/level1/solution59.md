# 프로그래머스 Level1 : 삼총사

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/131705)

```java
class Solution {
    public int solution(int[] number) {
        int answer = 0;
        int n = number.length; //학생수
        int sum = 0;
        for(int i=0; i<=n-2; i++){
            for(int j=i+1; j<=n-1; j++){
                for(int k=j+1; k<n; k++){
                    sum = number[i]+number[j]+number[k];
                    if(sum==0){
                        answer++;      
                    }
                    sum = 0;
                }
            }
        }
        return answer;
    }
}
```