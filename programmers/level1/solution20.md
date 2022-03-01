# 프로그래머스 Level1 : 연습문제 2016년

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12901)

```java
class Solution {
    public String solution(int a, int b) {
        String answer = "";
        String[] day = {"SUN","MON","TUE","WED","THU","FRI","SAT"};
        int days = 4;
        
        //1월 1일 = days[5]
        for(int i=1; i<a; i++){
            if(i==1 ||i==3||i==5||i==7||i==8|| i==10||i==12){
                days+=31;
            } else if(i==2){
                days+=29;
            } else {
                days+=30;
            }
        }
        
        days+=b;
        answer = day[days%7];
        
        return answer;
    }
}
```