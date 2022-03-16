# 프로그래머스 Level2 : 2018 KAKAO BLIND RECRUITMENT [3차] n진수 게임

- [문제](https://programmers.co.kr/learn/courses/30/lessons/17687)

```java
import java.util.Stack;
class Solution {
    String toNthNumber(int number, int n){
        StringBuilder sb = new StringBuilder();
        while(number>0){
            int m = number%n;
            if(m>=10) sb.insert(0,(char)('A'+m-10));
            else sb.insert(0,m);
                
            number/=n;
        }
        
        return sb.toString();
    }
    
    public String solution(int n, int t, int m, int p) {
        int order = 2;
        int number = 1;
        StringBuilder mine = new StringBuilder();
        if(p==1) mine.append(0);
        
        while(mine.length()<t){
            String strNum = toNthNumber(number++,n);
            for(int i=0; i<strNum.length(); i++){
                if(order==p) mine.append(strNum.charAt(i));
                if(mine.length()>=t) return mine.toString();
                order%=m;
                order++;
            }
        }
        
        return mine.toString();
    }
}
```