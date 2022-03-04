# 프로그래머스 Level2 : Summer/Winter Coding(2019) 멀쩡한 사각형

- [문제](https://programmers.co.kr/learn/courses/30/lessons/62048)

```java
class Solution {
    public long solution(int w, int h) {
        long answer = (long)w*h;
        int a = w<h?w:h;
        int b = w<h?h:w;
        int gcd = 0;    //최대공약수
        
        for(int i=a; i>0; i--){
            if(a%i==0&&b%i==0){
                gcd = i;
                break;
            }
        }
        
        // 한 사이클에서 선이 지나는 영역
        int area = (a/gcd)+(b/gcd)-1;

        answer -= (gcd*area);
        
        return answer;
    }
}
```