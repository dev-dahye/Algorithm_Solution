# 프로그래머스 Level1 : 2022 KAKAO BLIND RECRUITMENT 신고 결과 받기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/92334)

```java
import java.util.HashSet;
import java.util.Set;
import java.util.HashMap;
class Solution {
    public int[] solution(String[] id_list, String[] report, int k) {
        int l = id_list.length;
        int[] answer = new int[l];
        // 신고 당한 사람, 신고 횟수 
        HashMap<Integer,Integer> reported = new HashMap<>();
        // 신고한 사람, 신고당한 사람들
        HashMap<Integer, HashSet<Integer>> myReports =  new HashMap<>();
        
        for(String r : report){
            String[] user = r.split(" ");
            int me=-1; 
            int you=-1;
            
            for(int i=0; i<l; i++){
                if(id_list[i].equals(user[0])){
                    me = i; 
                } else if(id_list[i].equals(user[1])){
                    you = i; 
                }
                
                if(me!=-1&&you!=-1) 
                    break;   
            }
            
            if(myReports.get(me)==null){
                myReports.put(me, new HashSet<Integer>());
            }
            
            if(myReports.get(me).add(you)){
                reported.put(you, reported.getOrDefault(you, 0)+1);
            }
        }
        
        Set<Integer> keysReported = reported.keySet();
        Set<Integer> keysReports = myReports.keySet();
        for(int keyRed : keysReported){
            if(reported.get(keyRed)>=k){
                for(int keyRs: keysReports){
                    if(!myReports.get(keyRs).add(keyRed)){
                        answer[keyRs]++;
                    }
                }
            }
        }
        return answer;
    }
}
```