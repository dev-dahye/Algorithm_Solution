# 프로그래머스 Level1 : 크기가 작은 부분 문자열

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/147355)

```java
class Solution {
    public int solution(String t, String p) {
        int answer = 0;
        int size = p.length();
        for(int i=0; i<t.length()-size+1; i++){
            String sub = t.substring(i,i+size);
            if (Long.parseLong(sub)<=Long.parseLong(p)){
                answer++;
            }
        }
        return answer;
    }
}
```