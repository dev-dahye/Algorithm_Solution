# 프로그래머스 Level2 : 2018 KAKAO BLIND RECRUITMENT [3차] 압축

- [문제](https://programmers.co.kr/learn/courses/30/lessons/17684)

```java
import java.util.HashMap;
import java.util.ArrayList;
import java.util.Map;
class Solution {
    public int[] solution(String msg) {
        int len = msg.length();
        HashMap<String,Integer> dictionary = new HashMap<>();
        ArrayList<Integer> zip = new ArrayList<>();
        
        int index = 1;
        for(char c ='A'; c<='Z'; c++){
            dictionary.put(Character.toString(c),index++);
        }
        
        StringBuilder curr = new StringBuilder();
        
        for(int i=0; i<len; i++){
            StringBuilder prev = new StringBuilder();
            prev.append(curr);
            curr.append(msg.charAt(i));
            //System.out.println(curr.toString());
            
            if(dictionary.containsKey(curr.toString()) && i<len-1) continue;
            else if(dictionary.containsKey(curr.toString()) && i==len-1){
                zip.add(dictionary.get(curr.toString()));
            } else{
                zip.add(dictionary.get(prev.toString()));
                dictionary.put(curr.toString(),index++);
                curr.delete(0,curr.length());
                i--;
            }
        }
        
        int[] answer = new int[zip.size()];
        for(int i=0; i<zip.size(); i++){
            answer[i] = zip.get(i);
        }
        
        return answer;
    }
}
```