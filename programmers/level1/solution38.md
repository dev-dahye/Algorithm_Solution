# 프로그래머스 Level1 : 연습문제 시저 암호

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12926)

```java
class Solution {
    public String solution(String s, int n) {
        String answer = "";
        char[] cArr = s.toCharArray();
        int l = s.length();
        StringBuilder sb = new StringBuilder();
        
        for(int i=0; i<l; i++){
            if(cArr[i]!=' '){
                if(cArr[i]>='a' && cArr[i]<='z')
                    cArr[i] = cArr[i]+n>'z'? (char)(cArr[i]+n-26) : (char)(cArr[i]+n);    
                else if(cArr[i]>='A' && cArr[i]<='Z')
                    cArr[i] = cArr[i]+n>'Z'? (char)(cArr[i]+n-26) : (char)(cArr[i]+n);    
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