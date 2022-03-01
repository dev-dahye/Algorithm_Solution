# 프로그래머스 Level1 : 연습문제 가운데 글자 가져오기

- [문제]()

```java
class Solution {
    public String solution(String s) {
        String answer = "";
        int index = 0;
        int l = s.length();
        
        if(l%2==0){
            index=l/2-1;
            answer = s.substring(index,index+2);
        } else{
            index=l/2;
            answer = s.substring(index,index+1);
        }
        
        return answer;
    }
}
```