# 프로그래머스 Level1 : 2022 KAKAO BLIND RECRUITMENT 신고 결과 받기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/92334)

```java
import java.util.HashSet;
//import java.util.Set;
import java.util.HashMap;
import java.util.Map;

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
            int from=-1; 
            int to=-1;
            
            for(int i=0; i<l; i++){
                if(id_list[i].equals(user[0])){
                    from = i; 
                } else if(id_list[i].equals(user[1])){
                    to = i; 
                }
                
                if(from!=-1&&to!=-1) 
                    break;   
            }
            
            if(myReports.get(from)==null){
                myReports.put(from, new HashSet<Integer>());
            }
            
            if(myReports.get(from).add(to)){
                reported.put(to, reported.getOrDefault(to, 0)+1);
            }
        }
        
        /*
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
        }*/
        for(Map.Entry<Integer,Integer> entry: reported.entrySet()){
            if(entry.getValue()>=k){
                for(Map.Entry<Integer,HashSet<Integer>> entry1: myReports.entrySet()){
                    if(!entry1.getValue().add(entry.getKey())){
                        answer[entry1.getKey()]++;
                    }
                }
            }
        }
        return answer;
    }
}
```

```java
import java.util.HashSet;
import java.util.Set;
import java.util.HashMap;
import java.util.Map;


class Solution {
    public int[] solution(String[] id_list, String[] report, int k) {
        int l = id_list.length;
        int[] answer = new int[l];
        // 신고 당한 사람, 신고 횟수 
        HashMap<String,Integer> reported = new HashMap<>();
        // 회원, 회원의 신고한 회원 리스트
        HashMap<String, HashSet<String>> reports =  new HashMap<>();
        
        for(int i=0; i<l; i++){
            reports.put(id_list[i], new HashSet<String>());
        }
        
        for(String r : report){
            String[] users = r.split(" ");

            String from = users[0];
            String to = users[1];          
            
            if(reports.get(from).add(to)){
                reported.put(to, reported.getOrDefault(to, 0)+1);
            }
        }
        
        // 신고 한 유저 중 정지 아닌 유저 정리
        for(String r : report){

            String[] users = r.split(" ");

            String from = users[0];
            String to = users[1];

            // 정지 유저면
            if(reported.get(to) >= k)
                continue;

            reports.get(from).remove(to);
        }
        
        for(int i=0; i<l; i++){
            String id = id_list[i];
            answer[i] = reports.get(id).size();
        }

        return answer;
    }
}
```

## Map => entry로 조회

```java
for (Map.Entry<String,Integer> entry: map.entrySet()){
    System.out.println("[key] : " + entry.getKey() + " [value] : " + entry.getValue());
}

```

## Set => iterator 로 조회

```java
Iterator<Integer> iter = hSet.iterator();

while(iter.hasNext()){
    System.out.println(iter.next()); // 1 3 4 5 출
} 
```

<br>
<br>

- - -
## Reference
- <https://github.com/jki503/Algorithm_Solution/blob/main/programmers/level1/solution01.md>
- <https://github.com/jki503/CS_for-tech-interview/blob/main/dataStructure/README.md>