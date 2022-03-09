# 프로그래머스 Level2 : 해시 위장

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42578)

```java
import java.util.HashMap;
import java.util.Map;
import java.util.ArrayList;

class Solution {
    public int solution(String[][] clothes) {
        int answer = 1;
        HashMap<String,ArrayList<String>> spyWear = new HashMap<>();
        
        for(String[] c : clothes){
            ArrayList<String> list;
            if(spyWear.containsKey(c[1])){
                list = spyWear.get(c[1]);
            }else{
                list = new ArrayList<>();
            }
            list.add(c[0]);
            spyWear.put(c[1], list);   
        }
        
        //해당 의상종류를 안입을 경우까지 포함해서 계산
        //headgear: yellowhat, green_turban, none (3가지)
        //eyewear: bluesunglasses, none (2가지)
        // 최소 하나의 의상을 입어야함 (-아무것도 안입는 경우 1가지)
        for(Map.Entry<String,ArrayList<String>> entry : spyWear.entrySet()){
            ArrayList<String> list = entry.getValue();
            answer *= (list.size()+1);
        }
        
        return answer-1;
    }
}
```