# 프로그래머스 Level2 : 상담예약제

- [문제](https://school.programmers.co.kr/tryouts/78116/challenges)

```java
import java.time.*;
import java.util.*;
class Solution {
    public String[] solution(String[][] booked, String[][] unbooked) {
        ArrayList<String> nameList = new ArrayList<>();
        LocalTime bTime = LocalTime.of(23,59);
        LocalTime ubTime = LocalTime.of(23,59);
        LocalTime time = LocalTime.of(0,0); //현재 시간

        boolean isExistBooked = true;
        boolean isExistUnbooked = true;
        int bIndex = 0, ubIndex = 0;

        while(true){
            if(bIndex>=booked.length) {
                isExistBooked = false;
            }
            if(ubIndex>=unbooked.length) {
                isExistUnbooked = false;
            }

            // 기다리는 고객이 없으면 종료
            if((!isExistBooked) && (!isExistUnbooked)){
                break;
            }

            // 예약고객
            if(isExistBooked){
                String[] bStrTime = booked[bIndex][0].split(":");
                bTime = LocalTime.of(Integer.parseInt(bStrTime[0]),Integer.parseInt(bStrTime[1]));
            }
            // 일반고객
            if(isExistUnbooked){
                String[] ubStrTime = unbooked[ubIndex][0].split(":");
                ubTime = LocalTime.of(Integer.parseInt(ubStrTime[0]),Integer.parseInt(ubStrTime[1]));
            }

            // 첫손님 혹은 시간 텀을 두고 온 손님 
            if(!time.isAfter(bTime) && !time.isAfter(ubTime)){
                time = bTime.isBefore(ubTime)? LocalTime.of(bTime.getHour(),bTime.getMinute()) : LocalTime.of(ubTime.getHour(),ubTime.getMinute());
                if(bTime.isBefore(ubTime)){ //예약고객이 먼저왔으면
                    nameList.add(booked[bIndex++][1]);        
                } else{
                    nameList.add(unbooked[ubIndex++][1]);        
                }
                time = time.plusMinutes(10);
                continue;
            }

            if(isExistBooked){ // 예약고객이 있음 
                if(!time.isBefore(bTime)){ // 예약고객이 도착함 
                    nameList.add(booked[bIndex++][1]);        
                } else { 
                    if(isExistUnbooked && !time.isBefore(ubTime)){ // 일반 고객이 존재
                        nameList.add(unbooked[ubIndex++][1]);   
                    }
                }
                time = time.plusMinutes(10);
            } else { // 예약고객이 없음 
                // 남은 일반 고객을 순서대로 처리
                for(int i=ubIndex; i<unbooked.length; i++){
                    nameList.add(unbooked[i][1]);
                }
                break;
            }

        }

        String[] answer = new String[nameList.size()];
        for(int i=0; i<nameList.size(); i++){
            answer[i] = nameList.get(i);
        }
        return answer;
    }
}
```