# 프로그래머스 Level1 : 연습문제 콜라츠 추측

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12943)

```java
class Solution {
    public int solution(int num) {
        int answer = 0;
        long n = (long)num;
        
        while(answer<=500){
            if(n==1) break;
            else if(n%2==0) n/=2;  
            else n= n*3+1;  
    
            answer++;
        } 
        
        if(answer==501) 
            answer=-1;
        
        return answer;
    }
}
```