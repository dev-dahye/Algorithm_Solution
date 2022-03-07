# 프로그래머스 Level2 : 2019 카카오 개발자 겨울 인턴십 튜플

- [문제](https://programmers.co.kr/learn/courses/30/lessons/64065)

```java
import java.util.HashMap;
import java.util.Map;
class Solution {
    public int[] solution(String s) {
        HashMap<Integer, Integer> numMap = new HashMap<>();
        
        StringBuilder sb = new StringBuilder();
        for(char c : s.toCharArray()){
            if(c>='0'&&c<='9') sb.append(c);
            else if((c==','||c=='}')&&sb.length()!=0){
                int num = Integer.parseInt(sb.toString());
                numMap.put(num,numMap.getOrDefault(num,0)+1);
                sb.delete(0,sb.length());
            }
        }
        
        int[] answer = new int[numMap.size()];
        for(Map.Entry<Integer,Integer> entry : numMap.entrySet()){
            answer[numMap.size()-entry.getValue()] = entry.getKey();
        }
        
        return answer;
    }
}
```