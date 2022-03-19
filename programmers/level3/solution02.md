# 프로그래머스 Level3 : 2018 KAKAO BLIND RECRUITMENT [1차] 추석 트래픽

- [문제](https://programmers.co.kr/learn/courses/30/lessons/17676)

```java
import java.util.ArrayList;
import java.util.Comparator;
import java.util.Collections;

class Solution {
    public int solution(String[] lines) {
        int answer = 0;
        ArrayList<long[]> timeLine = new ArrayList<>();
        
        for(String l : lines){
            String[] arr = l.split(" ");
            String[] time = arr[1].split(":");
            long hour = Long.parseLong(time[0])*1000;
            long minute = Long.parseLong(time[1])*1000;
            long second = (long)(Double.parseDouble(time[2])*1000);
            
            long eTime = hour*3600 + minute*60 + second;
            long sTime = eTime-(long)(Double.parseDouble(arr[2].replace("s",""))*1000)+1;
            
            long[] tl = {sTime,eTime};
            timeLine.add(tl);
        }
        
        
        Collections.sort(timeLine, new Comparator<long[]>(){
            @Override
            public int compare(long[] t1, long[] t2){
                return t1[0]>t2[0]?1:-1;
            }
        });
             
        
        
        for(int i=0; i<timeLine.size(); i++){
            int cnt = 0;
            long cTime = timeLine.get(i)[1];
            long cTimeTo1Sec = cTime+999;

            for(int j=0; j<timeLine.size(); j++){
                long sTime = timeLine.get(j)[0];
                long eTime = timeLine.get(j)[1];

                if(cTime<=sTime && cTimeTo1Sec>=sTime){
                    cnt++;   
                } else if(cTime<=eTime && cTimeTo1Sec>=eTime){
                    cnt++; 
                } else if(sTime<=cTime && eTime>=cTimeTo1Sec){
                    cnt++; 
                }else if(cTimeTo1Sec<sTime){
                    break;
                }
            }
            answer = Math.max(answer,cnt);
        }
        
        
        return answer;
    }
}
```

## LocalDateTime
```java
import java.util.ArrayList;
import java.util.Comparator;
import java.util.Collections;
import java.time.LocalDateTime;
import java.time.LocalTime;
import java.time.format.DateTimeFormatter;

class Solution {
    public int solution(String[] lines) {
        int answer = 0;
        ArrayList<LocalDateTime[]> timeLine = new ArrayList<>();
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-ddHH:mm:ss.SSS");
        
        for(String l : lines){
            String[] arr = l.split(" ");
            
            LocalDateTime eTime = LocalDateTime.parse(arr[0]+arr[1], formatter);
            LocalDateTime sTime = eTime.minusNanos((long)(Double.parseDouble(arr[2].replace("s",""))*1000000000)-1000000);
            sTime = sTime.withNano((int)(sTime.getNano()/1000000)*1000000);
            LocalDateTime[] tl = {sTime,eTime};
            timeLine.add(tl);
            
        }
        
        Collections.sort(timeLine, new Comparator<LocalDateTime[]>(){
            @Override
            public int compare(LocalDateTime[] t1, LocalDateTime[] t2){
                return t1[0].isBefore(t2[0])? -1 : 1;
            }
        });
                
        for(int i=0; i<timeLine.size(); i++){
            int cnt = 0;
            LocalDateTime cTime = timeLine.get(i)[1];
            LocalDateTime cTimeTo1Sec = cTime.plusNanos(999000000);
            
            for(int j=0; j<timeLine.size(); j++){
                LocalDateTime sTime = timeLine.get(j)[0];
                LocalDateTime eTime = timeLine.get(j)[1];
                
                if(cTimeTo1Sec.isBefore(sTime)){
                    break;
                } else if(eTime.isBefore(cTime)){
                    continue;
                }
                cnt++;
                
            }
            answer = Math.max(answer,cnt);
        }
        
        
        return answer;
    }
}
```