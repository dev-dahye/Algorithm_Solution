# 프로그래머스 Level1 : 연습문제 서울에서 김서방 찾기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12919)

```java
class Solution {
    public String solution(String[] seoul) {
        int answer = 0;
        for(int i=0; i<seoul.length; i++){
            if(seoul[i].equals("Kim")){
                answer = i;
                break;
            }
        }
        
        return "김서방은 "+answer+"에 있다";
    }
}
```