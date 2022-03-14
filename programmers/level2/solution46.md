# 프로그래머스 Level2 : 2018 KAKAO BLIND RECRUITMENT [1차] 캐시

- [문제](https://programmers.co.kr/learn/courses/30/lessons/17680#)

```java
import java.util.HashMap;
import java.util.Map;
class Solution {
    public int solution(int cacheSize, String[] cities) {
        int answer = 0;
        HashMap<String, Integer> cache = new HashMap<>();
        
        for(String city : cities){
            city = city.toLowerCase();
            String lru = "";
            if(cache.isEmpty()){
                answer += 5;
                cache.put(city,0);
            }else{
                for(Map.Entry<String, Integer> entry : cache.entrySet()){
                    cache.put(entry.getKey(),entry.getValue()+1);
                    if(lru.equals("")) lru = entry.getKey();
                    else lru = cache.get(lru) < entry.getValue()? entry.getKey() : lru;
                }    
               
                if(cacheSize == 0) answer += 5;
                else if(cache.containsKey(city)){
                    answer += 1;
                    cache.put(city,0);
                } else{
                    answer += 5;
                    if(cache.size()>=cacheSize){
                        cache.remove(lru);
                    } 
                    cache.put(city,0);
                }
            }
        }
        
        return answer;
    }
}
```