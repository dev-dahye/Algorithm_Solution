# 프로그래머스 Level2 : 2018 KAKAO BLIND RECRUITMENT [3차] 방금그곡

- [문제](https://programmers.co.kr/learn/courses/30/lessons/17683)

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public String solution(String m, String[] musicinfos) {
        String answer = "(None)";
        Integer maxLen = 0;
        
        HashMap<String,Object[]> music = new HashMap<>();

        m = m.replace("C#","V");
        m = m.replace("D#","W");
        m = m.replace("F#","X");
        m = m.replace("G#","Y");
        m = m.replace("A#","Z");
        
        for(String str : musicinfos){
            String[] arr = str.split(",");
            String[] sTime = arr[0].split(":");
            String[] eTime = arr[1].split(":");
            
            // 라디오 재생시간
            Integer time = (Integer.parseInt(eTime[0])-Integer.parseInt(sTime[0]))*60;
            time += Integer.parseInt(eTime[1])-Integer.parseInt(sTime[1]);
            
            // 노래제목
            String name = arr[2];
            
            arr[3] = arr[3].replace("C#","V");
            arr[3] = arr[3].replace("D#","W");
            arr[3] = arr[3].replace("F#","X");
            arr[3] = arr[3].replace("G#","Y");
            arr[3] = arr[3].replace("A#","Z");
            
            // 라디오에서 재생된 노래부분
            String melody = arr[3];
            int len = melody.length();
            StringBuilder sb = new StringBuilder();
            for(int t=0; t<time; t++){
                sb.append(melody.charAt(t%len));
            }
            melody = sb.toString();
            
            Object[] info = {name,time};
            if(!music.containsKey(melody) || (music.containsKey(melody) && (Integer)music.get(melody)[1]<time)) 
                music.put(melody,info);
        }
        
        for(Map.Entry<String,Object[]> entry: music.entrySet()){
            if(entry.getKey().contains(m)){
                Integer l = (Integer)entry.getValue()[1];
                if(maxLen<l){
                    maxLen = l;
                    answer = (String)entry.getValue()[0];
                }
            }
        }
        
        return answer;
    }
}
```