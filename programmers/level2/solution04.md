# 프로그래머스 Level2 : 2020 KAKAO BLIND RECRUITMENT 문자열 압축

- [문제](https://programmers.co.kr/learn/courses/30/lessons/60057)

```java
import java.util.ArrayList;
class Solution {
    public int solution(String s) {        
        int l = s.length();
        int answer = l;
        ArrayList<String> strs = new ArrayList<>();
        StringBuilder sb = new StringBuilder();
        String str = "";
        String nextStr = "";
        int zip = 1;

        for(int i=1; i<=l; i++){    //몇개씩 묶을지
            for(int j=0; j<l; j+=i){ // 문자열 조회
                str = i+j<=l ? s.substring(j,i+j) : s.substring(j); // 마지막으로 잘라낸 문자열은 길이 상관X
                strs.add(str); 
                str="";
            }
            
            // 반복되는 문자열 확인해서 sb에 추가
            nextStr = strs.get(0);
            zip = 1;
            for(int k=1; k<strs.size(); k++){
                if(nextStr.equals(strs.get(k))){
                    zip++;
                } else{
                    if(zip!=1) sb.append(zip);
                    sb.append(nextStr);
                    nextStr = strs.get(k);
                    zip = 1;
                }
            }
            if(zip!=1) sb.append(zip);
            sb.append(nextStr);
            
            answer = answer>sb.length()?sb.length():answer;
            
            sb.delete(0,sb.length());
            strs.clear();
        }
        
        return answer;
    }
}
```