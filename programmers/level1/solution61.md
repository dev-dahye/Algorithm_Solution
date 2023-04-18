# 프로그래머스 Level1 : 콜라 문제

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/132267)

```java
class Solution {
    public int solution(int a, int b, int n) {
        int answer = 0;
        while(n>=a){
            int change = (n/a)*b;
            n = n%a+change;
            
            answer += change;
        }
        return answer;
    }
}
```