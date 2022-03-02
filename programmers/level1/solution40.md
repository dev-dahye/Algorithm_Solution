# 프로그래머스 Level1 : 연습문제 이상한 문자 만들기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12930)

```java
class Solution {
    public String solution(String s) {
        String answer = "";
        int l = s.length();
        int odd = 1;
        char[] cArr = s.toCharArray();
        StringBuilder sb = new StringBuilder();
        
        for(int i=0; i<l; i++){
            if(cArr[i]==' '){
                odd = 1;
            }else{
                if(odd==1)
                    cArr[i] = cArr[i]>='a'&&cArr[i]<='z'? (char)(cArr[i]-('a'-'A')) : cArr[i];
                else
                    cArr[i] = cArr[i]>='A'&&cArr[i]<='Z'? (char)(cArr[i]+('a'-'A')) : cArr[i];
                
                odd*=-1;
            }
        }
        
        for(char c : cArr){
            sb.append(c);
        }
        answer = sb.toString();
        
        return answer;
    }
}
```