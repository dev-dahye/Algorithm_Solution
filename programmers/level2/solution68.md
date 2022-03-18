# 프로그래머스 Level2 : 연습문제 N개의 최소공배수

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12953)

```java
import java.util.ArrayList;
class Solution {
    int lcm(int num1, int num2){
        int a = Math.min(num1,num2);
        int b = Math.max(num1,num2);
        int gcd = 1;
        for(int i=a; i>0; i--){
            if(a%i==0&&b%i==0){
                gcd = i;
                break;
            }
        }
        return a/gcd*b;
    }
    
    public int solution(int[] arr) {
        int answer = 0;
        ArrayList<Integer> numList = new ArrayList<>();
        for(int i : arr){
            numList.add(i);
        }
        
        while(numList.size()>1){
            numList.add(lcm(numList.get(0),numList.get(1)));
            numList.remove(0);
            numList.remove(0);
        }
        
        return numList.get(0);
    }
}
```