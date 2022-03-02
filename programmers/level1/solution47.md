# 프로그래머스 Level1 : 연습문제 최대공약수와 최소공배수

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12940)

```java
class Solution {
    public int[] solution(int n, int m) {
        int[] answer = new int[2];
        // n*m = 최대공약수 * 최소공배수
        int a = n<m?n:m;
        int b = n<m?m:n;
        for(int i=a; i>0; i--){
            if(a%i==0 && b%i==0){
                answer[0] = i;
                break;
            }
        }
        
        answer[1] = n*m / answer[0];
        return answer;
    }
}
```