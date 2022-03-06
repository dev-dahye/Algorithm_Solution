# 프로그래머스 Level2 : 2020 KAKAO BLIND RECRUITMENT 괄호 변환

- [문제](https://programmers.co.kr/learn/courses/30/lessons/60058)

```java
import java.util.Stack;
class Solution {
     boolean isCorrectString(String w){ // 올바른 문자열인지 확인
        Stack<Character> stack = new Stack<>();
        
        for(char c : w.toCharArray()){
            if(c=='(') stack.push('(');
            else{
                if(!stack.isEmpty()){
                    stack.pop();
                } else { 
                    return false;
                }
            }    
        }
        if(!stack.isEmpty()){
            return false;
        } else{
            return true;
        }
     }
    
    String fixString(String w){
        int l = 0;  //'(' 갯수
        int r = 0;  //')' 갯수
        if(isCorrectString(w)) return w;
        
        //2
        int length = w.length();
        StringBuilder u = new StringBuilder();
        StringBuilder v = new StringBuilder();
        for(int i=0; i<length; i++){
            if(w.charAt(i)=='('){
                l++;
                u.append('(');
            } else{
                r++;  
                u.append(')');
            } 

            if(l==r){
                for(int j=i+1; j<length; j++){
                    v.append(w.charAt(j));
                }                
                break;
            }
        }
        
        //3
        if(isCorrectString(u.toString())){
            //3-1
            return u.append(fixString(v.toString())).toString();
        } else{ //4
            //4-1, 4-2, 4-3
            StringBuilder str = new StringBuilder();
            str.append('(');
            str.append(fixString(v.toString()));
            str.append(')');
            
            //4-4. 
            StringBuilder newU = new StringBuilder();
            for(int i=1; i<u.length()-1; i++){
                if(u.charAt(i)=='(') newU.append(')');
                else newU.append('(');
            }
            
            return str.append(newU).toString();
        }
    }
    
    public String solution(String p) {
        return fixString(p);
    }
}
```