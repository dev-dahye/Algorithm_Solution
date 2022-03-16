# 프로그래머스 Level2 : 연습문제 다음 큰 숫자

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12911)

```java
class Solution {
    int cntOne(int n){
        String binary = Integer.toBinaryString(n);
        int cnt = 0;
        for(char c : binary.toCharArray()){
            if(c == '1') cnt++;
        }
        return cnt;
    }
    
    public int solution(int n) {
        int cnt = cntOne(n);
        while(true){
            if(cnt == cntOne(++n)){
                return n;
            }
        }
        
    }
    
}
```
