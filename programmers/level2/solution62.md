# 프로그래머스 Level2 : 2022 KAKAO BLIND RECRUITMENT 주차 요금 계산

- [문제](https://programmers.co.kr/learn/courses/30/lessons/92341)

```java
import java.util.HashMap;
import java.util.Map;
import java.util.Arrays;

class Solution {
    public int[] solution(int[] fees, String[] records) {
        HashMap<String,String> carMap = new HashMap<>();
        HashMap<String,Integer> feeMap = new HashMap<>();
        
        for(String r : records){
            String[] info = r.split(" ");
            String time = info[0];
            String carNumber = info[1];
            String inOut = info[2];
            
            if(!carMap.containsKey(carNumber) && inOut.equals("IN")){   
                carMap.put(carNumber,time);
            } else if(carMap.containsKey(carNumber) && inOut.equals("OUT")){
                String[] inTime = carMap.get(carNumber).split(":");
                String[] outTime = time.split(":");
                carMap.remove(carNumber);
                
                int pTime = (Integer.parseInt(outTime[0])-Integer.parseInt(inTime[0]))*60 + Integer.parseInt(outTime[1])-Integer.parseInt(inTime[1]);
                
                int t = feeMap.containsKey(carNumber)?feeMap.get(carNumber) : 0;
                feeMap.put(carNumber,pTime+t);
            }
        }
        
        for(Map.Entry<String, String> entry : carMap.entrySet()){
            String[] inTime = entry.getValue().split(":");
            int pTime = (23-Integer.parseInt(inTime[0]))*60 + 59-Integer.parseInt(inTime[1]);
            
            int t = feeMap.containsKey(entry.getKey())?feeMap.get(entry.getKey()) : 0;
            feeMap.put(entry.getKey(),pTime+t);
        }
        
        
        for(Map.Entry<String, Integer> entry : feeMap.entrySet()){
            if(entry.getValue()<=fees[0]) {
                feeMap.put(entry.getKey(),fees[1]);
            }else{
                int fee = fees[1] + (int)Math.ceil((double)(entry.getValue()-fees[0])/fees[2]) * fees[3];
                feeMap.put(entry.getKey(),fee);
            }
        }
        
        Object[] key = feeMap.keySet().toArray();
        Arrays.sort(key);
        int[] answer = new int[key.length];
        for(int i=0; i<key.length; i++){
            answer[i] = feeMap.get((String)key[i]);
        }
        
        return answer;
    }
}
```