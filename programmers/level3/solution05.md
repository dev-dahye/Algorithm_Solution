# 프로그래머스 Level3 : Summer/Winter Coding(~2018) : 기지국 설치

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/12979)

#### HashMap 이용: 효율성테스트 0점 
```java
import java.util.*;
class Solution {
    public int solution(int n, int[] stations, int w) {
        int answer = 0;
        HashMap<Integer,Boolean> apartMap = new HashMap<>();
        for(int i=1; i<=n; i++){
            apartMap.put(i,false);
        }

        for(int s: stations){
            apartMap.replace(s,true);
            for(int i=1; i<=w; i++){
                apartMap.replace(s+i,true);
                apartMap.replace(s-i,true);
            }
        }

        for(int j : apartMap.keySet()){
            if(!apartMap.get(j)){
                int k = j+w;
                apartMap.replace(k,true);
                answer++;
                for(int i=1; i<=w; i++){
                    apartMap.replace(k+i,true);
                    apartMap.replace(k-i,true);
               }
            }
        }     
        return answer;
    }
}
```
### Math.ceil
```java
class Solution {    // 범위가 닿지 않는 구간에 최소의 기지국을 세우는 방법
    public int solution(int n, int[] stations, int w) {
        int answer = 0;
        int sIndex = 0;
        int station = stations[0];
        for(int i=1; i<=n;){
            if(i>station+w){   
                if(sIndex<stations.length-1){
                    station = stations[++sIndex];
                } else if(sIndex==stations.length-1){
                    answer += Math.ceil((float)(n-i+1)/(2*w+1));
                    break;
                }
            }
            if(i>=station-w && i<=station+w){
                i=station+w+1;
            } else {
                answer += Math.ceil((float)(station-w-i)/(2*w+1));
                i = station+w+1;   
            }
            
        }
        return answer;
    }
}
```

### Greedy
```java
class Solution {
    public int solution(int n, int[] stations, int w) {
        int answer = 0;
        int sIndex = 0;
        int station = stations[0];  // 이미 설치된 기지국 중 가까운 곳
        
        for(int i=1; i<=n;){    // i = 현재 위치
            if(i>=station-w && i<=station+w){   //station범위안에 있다면
                i = station+w+1;                //이미설치된 기지국 밖으로 이동
                if(sIndex<stations.length-1){   // 다음 station 확인
                    station = stations[++sIndex];
                } else{
                    station = n+w+1;
                }
            } else {        //전파가 닿지 않으면
                answer++;   //i에서 전파범위만큼 이동해서 세우기 i를 전파범위 다음으로 이동 
                i += 2*w+1;
            }
        }
        return answer;
    }
}
```