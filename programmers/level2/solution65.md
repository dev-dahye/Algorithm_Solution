# 프로그래머스 Level2 : 연습문제 피보나치 수

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12945)

```java
import java.util.ArrayList;
class Solution {
    public int solution(int n) {
        int answer = 0;
        ArrayList<Integer> ArrayList = new ArrayList<>();
        ArrayList.add(0);
        ArrayList.add(1);
        
        //(A + B) % C ≡ ( ( A % C ) + ( B % C) ) % C
        for(int i=2; i<=n; i++){
            ArrayList.add((ArrayList.get(i-1)%1234567+ArrayList.get(i-2)%1234567)%1234567);
        }

        answer = ArrayList.get(n);
        
        return answer;
    }
}   
```