# 프로그래머스 Level2 : 2018 KAKAO BLIND RECRUITMENT [1차] 뉴스 클러스터링

- [문제](https://programmers.co.kr/learn/courses/30/lessons/17677)

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.Map;
class Solution {
    double jaccard(HashMap<String,Integer> strMap1, HashMap<String,Integer> strMap2){
        HashMap<String,Integer> itstion = new HashMap<>();      // 교집합 intersection
        HashMap<String,Integer> union = new HashMap<>();        // 합집합
        
        for(Map.Entry<String, Integer> entry: strMap1.entrySet()){
            if(strMap2.containsKey(entry.getKey())){
                int val = strMap2.get(entry.getKey());
                int min = val>entry.getValue()?entry.getValue():val;
                int max = val<entry.getValue()?entry.getValue():val;
                itstion.put(entry.getKey(),min);
                union.put(entry.getKey(),max);
            } else{
                union.put(entry.getKey(),entry.getValue());
            }
        }
        
        for(Map.Entry<String, Integer> entry: strMap2.entrySet()){
            if(!union.containsKey(entry.getKey())){
                union.put(entry.getKey(),entry.getValue());
            }
        }
        
        double jaccard = 1.0;
        int iSize = 0;
        int uSize = 0;
        
        for(Map.Entry<String, Integer> entry: itstion.entrySet()){
            iSize += entry.getValue();
        }

        for(Map.Entry<String, Integer> entry: union.entrySet()){
            uSize += entry.getValue();
        }
        
        jaccard = (double)iSize / uSize;
        return jaccard;
    }
    
    public int solution(String str1, String str2) {
        int answer = 0;
        
        str1 = str1.toLowerCase();
        str2 = str2.toLowerCase();
        
        HashMap<String,Integer> strMap1 = new HashMap<>();
        HashMap<String,Integer> strMap2 = new HashMap<>();

        StringBuilder sb = new StringBuilder();
        for(int i=0; i<str1.length()-1; i++){
            char c1 = str1.charAt(i);
            char c2 = str1.charAt(i+1);
            if(c1>='a'&&c1<='z'&&c2>='a'&&c2<='z'){
                sb.append(c1);
                sb.append(c2);
                String str = sb.toString();
                strMap1.put(str,strMap1.getOrDefault(str,0)+1);
            }
            sb.delete(0,2);
        }
        
        for(int i=0; i<str2.length()-1; i++){
            char c1 = str2.charAt(i);
            char c2 = str2.charAt(i+1);
            if(c1>='a'&&c1<='z'&&c2>='a'&&c2<='z'){
                sb.append(c1);
                sb.append(c2);
                
                String str = sb.toString();
                strMap2.put(str,strMap2.getOrDefault(str,0)+1);
            }
            sb.delete(0,2);
        }
        
        if(strMap1.size()==0 && strMap2.size()==0) return 65536;
        answer = (int)(jaccard(strMap1,strMap2)*65536);
        
        return answer;
    }
}
```