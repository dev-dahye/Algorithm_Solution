# 프로그래머스 Level2 : 2021 KAKAO BLIND RECRUITMENT 메뉴 리뉴얼

- [문제](https://programmers.co.kr/learn/courses/30/lessons/72411)

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.Map;
import java.util.Collections;
import java.util.Arrays;

class Solution {
    ArrayList<String> answerList = new ArrayList<>();
    HashMap<String,Integer> courseMap = new HashMap<>();
    
    void combination(String foods, int index, boolean[] isVisited, char[] order, int course){     
        Arrays.sort(order);
        if(foods.length() == course){
            courseMap.put(foods,courseMap.getOrDefault(foods,0) +1);
            return;
        } else{
            for(int i=index; i<order.length; i++){
                if(!isVisited[i]){
                    isVisited[i] = true;
                    combination(foods+order[i],i,isVisited, order, course);    
                    isVisited[i] = false;
                }
            }
        }
    }
    
    public String[] solution(String[] orders, int[] course) {
        //코스의 음식 갯수별 음식조합 
        for(int c : course){
            for(String order : orders){
                boolean[] isVisited = new boolean[order.length()];
                combination("",0,isVisited,order.toCharArray(),c);   
            }
            
            int max = 0;
            for(Map.Entry<String,Integer> entry : courseMap.entrySet()){
                if(entry.getValue()>=2){
                    max = max<entry.getValue()?entry.getValue():max;
                }            
            }
            for(Map.Entry<String,Integer> entry : courseMap.entrySet()){
                if(entry.getValue()==max){
                    answerList.add(entry.getKey());
                
                }
            }
            
            courseMap.clear();
        }
        
        
        Collections.sort(answerList);
        String[] answer = new String[answerList.size()];
        int i = 0;
        for(String a: answerList){
            answer[i++] = a;
        }
        return answer;
    }
}
```