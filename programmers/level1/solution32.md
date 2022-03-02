# 프로그래머스 Level1 : 연습문제 문자열 내림차순으로 배치하기
- [문제](https://programmers.co.kr/learn/courses/30/lessons/12917)

```java
import java.util.Arrays;
import java.util.Comparator;

class Solution {
    public String solution(String s) {
        String answer = "";
        Character[] charArr = new Character[s.length()];
        StringBuilder sb = new StringBuilder();
        
        for(int i=0; i<s.length(); i++){
            charArr[i] = (Character)s.charAt(i);
        }
        
        Arrays.sort(charArr, new Comparator<Character>(){
            @Override
            public int compare(Character c1, Character c2){
                return c2-c1;
            }
        });
        
        for(char c : charArr){
            sb.append(c);
        }
        
        answer = sb.toString();
        return answer;
    }
}
```