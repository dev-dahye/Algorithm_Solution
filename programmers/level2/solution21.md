# 프로그래머스 Level2 : 2020 카카오 인턴십 수식 최대화

- [문제](https://programmers.co.kr/learn/courses/30/lessons/67257)

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.Map;
class Solution {
    // 0:'+' 1:'-' 2:'*'
    boolean[] isVisited = new boolean[3];
    String[] oper = {"+","-","*"};
    long max = 0;
    
    //연산자 순위 만들기
    void dfs(String prior, ArrayList<Long> operand, ArrayList<Character> operator){ 
        if(prior.length()==3){
            long cal = calculate(prior,operand,operator);
            max = max>cal?max:cal;
            return;
        } else{
            for(int i=0; i<3; i++){
                if(!isVisited[i]){
                    isVisited[i] = true;
                    dfs(prior+oper[i],operand,operator);
                    isVisited[i] = false;
                }
            }
        }
    }
    
    // 계산하기
    long calculate(String prior, ArrayList<Long> operand, ArrayList<Character> operator){
        ArrayList<Long> operd = new ArrayList<>(operand);
        ArrayList<Character> optor = new ArrayList<>(operator);
        
        for(char op : prior.toCharArray()){
            for(int i=0; i<optor.size(); i++){
                if(op==optor.get(i)){
                    if(op=='+') operd.add(i,operd.get(i)+operd.get(i+1));
                    else if(op=='-') operd.add(i,operd.get(i)-operd.get(i+1));
                    else operd.add(i,operd.get(i)*operd.get(i+1));
                    operd.remove(i+1);
                    operd.remove(i+1);
                    optor.remove(i);
                    i=-1;
                }
            }
        }
        
        return Math.abs(operd.get(0));
    }
    
    public long solution(String expression) {
        ArrayList<Long> operand = new ArrayList<>();
        ArrayList<Character> operator = new ArrayList<>();
        
        StringBuilder sb = new StringBuilder();
        for(char c : expression.toCharArray()){
            if(c=='+'||c=='-'||c=='*'){
                operand.add(Long.parseLong(sb.toString()));
                operator.add(c);
                sb.delete(0,sb.length());
            } else{
                sb.append(c);   
            }
        }
        operand.add(Long.parseLong(sb.toString()));
        
        dfs("",operand,operator);
        
        return max;
    }
}
```