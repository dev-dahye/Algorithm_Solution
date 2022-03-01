# 프로그래머스 Level1 : 월간 코드 챌린지 시즌2 약수의 개수와 덧셈

- [문제](https://programmers.co.kr/learn/courses/30/lessons/77884)

```java
class Solution {
    public int solution(int left, int right) {
        int answer = 0;
        int[] divisor = new int[right-left+1];
        for(int i=left; i<=right; i++){
            if(i%Math.sqrt(i)==0){
                answer -=i;
            } else{
                answer +=i;
            }
        }

        return answer;
    }
}
```