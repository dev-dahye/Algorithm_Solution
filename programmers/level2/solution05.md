# 프로그래머스 Level2 : 2019 KAKAO BLIND RECRUITMENT 오픈채팅방

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42888#)

```java
import java.util.HashMap;
import java.util.ArrayList;
class Solution {
    public String[] solution(String[] record) {
        String[] answer = {};            
        String behavior, uid, nickname;
        // uid, nickname
        HashMap<String, String> nicknameMap = new HashMap<>();
        // uid, behavior
        ArrayList<String[]> behaviorArray = new ArrayList<>();
        
        int index = 0;
        for(String r : record){
            String[] strs = r.split(" ");
            behavior = strs[0];
            uid = strs[1];
            nickname = behavior.equals("Leave")? "": strs[2];

            switch(behavior){
                case "Enter":
                    nicknameMap.put(uid,nickname);
                    behaviorArray.add(new String[2]);
                    behaviorArray.get(index)[0] = uid;
                    behaviorArray.get(index++)[1] = behavior;
                    break;
                case "Leave":   
                    behaviorArray.add(new String[2]);
                    behaviorArray.get(index)[0] = uid;
                    behaviorArray.get(index++)[1] = behavior;
                    break;
                case "Change":   
                    nicknameMap.put(uid,nickname);
                    break;
            }
        }
        
        answer = new String[behaviorArray.size()];
        int i = 0;
        for(String[] array : behaviorArray){
            StringBuilder sb = new StringBuilder();
            sb.append(nicknameMap.get(array[0]));
            sb.append("님이 ");
            if(array[1].equals("Enter")) sb.append("들어왔습니다.");
            else sb.append("나갔습니다.");
            answer[i++] = sb.toString();
        }
        
        return answer;
    }
}
```