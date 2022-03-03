# 프로그래머스 Level1 : 연습문제 하샤드 수

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12947)

```java
class Solution {
    public boolean solution(int x) {
        boolean answer = false;
        int num = x;
        int sum = 0;
        
        while(num!=0){
            sum += num%10;
            num/=10;
        }
        if(x%sum==0) 
            answer=true;
        
        return answer;
    }
}
```