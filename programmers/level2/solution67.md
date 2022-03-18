# 프로그래머스 Level2 : 연습문제 JadenCase 문자열 만들기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12951)

```java
class Solution {
    public String solution(String s) {
        String answer = "";
        boolean isFirst= false;
        StringBuilder sb = new StringBuilder();
        sb.append(Character.isDigit(s.charAt(0))?s.charAt(0) : Character.toUpperCase(s.charAt(0)));
        
        for(int i=1; i<s.length(); i++){
            if(s.charAt(i)==' '){
                isFirst = true;
                sb.append(' ');
                continue;
            }
            
            if(isFirst){
                sb.append(Character.isDigit(s.charAt(i))?s.charAt(i) : Character.toUpperCase(s.charAt(i)));
                isFirst=false;
            } else{
                sb.append(Character.toLowerCase(s.charAt(i)));
            }
        }
        
        return sb.toString();
    }
}
```