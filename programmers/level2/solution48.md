# 프로그래머스 Level2 : Summer/Winter Coding(~2018) 점프와 순간 이동

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12980)

```java
public class Solution {
    public int solution(int n) {
        int answer = 0;
        
        while(n!=0){
            if(n%2!=0){
                answer++;
                n--;
            }
            n=n/2;
        }

        return answer;
    }
}
```