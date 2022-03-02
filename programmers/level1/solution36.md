# 프로그래머스 Level1 : 연습문제 수박수박수박수박수박수?

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12922)

```java
class Solution {
    public String solution(int n) {
        String answer = "";
        StringBuilder sb = new StringBuilder();
        
        for(int i=0; i<n/2; i++){
            sb.append("수박");   
        }
        
        if(n%2 != 0)
            sb.append("수");  
        
        
        answer = sb.toString();
        return answer;
    }
}
```