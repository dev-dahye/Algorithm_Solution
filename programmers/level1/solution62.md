# 프로그래머스 Level1 : 푸드 파이트 대회

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/134240)

```java
class Solution {
    public String solution(int[] food) {
        StringBuffer answer = new StringBuffer("0");
        for(int i=food.length-1; i>=0; i--){
            for(int j=0;j<food[i]/2; j++){
                answer.append(i);
                answer.insert(0,i);
            }
        }
        return answer.toString();
    }
}
```