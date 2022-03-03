# 프로그래머스 Level1 : 연습문제 핸드폰 번호 가리기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12948)

```java
class Solution {
    public String solution(String phone_number) {
        String answer = "";
        StringBuilder sb = new StringBuilder();
        int l = phone_number.length();
        
        for(int i=0; i<l; i++){
            if(i<l-4){
                sb.append("*");
            } else{
                sb.append(phone_number.charAt(i));
            }
        }
        
        answer = sb.toString();
        return answer;
    }
}
```