# 프로그래머스 Level1 :해시 완주하지 못한 선수

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42576)

```java
import java.util.HashMap;
import java.util.Set;

class Solution {
    public String solution(String[] participant, String[] completion) {
        String answer = "";
        HashMap<String, Integer> pMap = new HashMap<String, Integer>();
        
        for(String p : participant){
            pMap.put(p,pMap.getOrDefault(p,0)+1);
        }
        
        for(String c: completion){
            pMap.put(c,pMap.get(c)-1);
        }
        
        Set<String> keys = pMap.keySet();  
        for(String key : keys){
            if(pMap.get(key) == 1){
                answer = key;
                break;
            }
        }
        
        return answer;
    }
}
```


<br>
<br>

- - -

## Refernce
- <https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html>