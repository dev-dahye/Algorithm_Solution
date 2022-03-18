# 프로그래머스 Level2 : 2022 KAKAO BLIND RECRUITMENT 양궁대회

- [문제](https://programmers.co.kr/learn/courses/30/lessons/92342)

```java
import java.util.HashMap;
import java.util.Arrays;
class Solution {
    HashMap<Integer,int[]> scoreMap = new HashMap<>();
    void shot(int[] score, int shot, int depth, int n, int[] info){
        if(depth==10 && shot!=n){
            score[10] = n-shot;
            shot = n;
        }
        if(shot==n){
            int s = calScore(info,score);
            if(scoreMap.containsKey(s)){
                int[] sArr = scoreMap.get(s);
                for(int i=10; i>=0; i--){
                    if(sArr[i]<score[i]){
                        scoreMap.put(s,score);
                        break;
                    }else if(sArr[i]>score[i]){
                        break;
                    }
                }   
            } else scoreMap.put(s,score);
            return;
        } else{
            int aScore = info[depth];
            
            int[] newScore1 = new int[11];
            for(int i=0; i<11; i++){
                newScore1[i] = score[i];
            }
            shot(newScore1, shot, depth+1, n, info);
            
            if(aScore+1<=(n-shot)){
                int[] newScore2 = new int[11];
                for(int i=0; i<11; i++){
                    newScore2[i] = score[i];
                }
                
                newScore2[depth] = aScore+1;
                shot(newScore2, shot+aScore+1, depth+1, n, info);
            }
            
        }
    }
    
    int calScore(int[] info, int[] score){
        int apeach = 0;
        int lion = 0;
        
        for(int i=0; i<10; i++){
            if(info[i]!=0 && info[i]>=score[i]) apeach+=10-i;
            else if(info[i]<score[i]) lion+=10-i;
        }
        
        return lion<=apeach? -1 : lion-apeach;
    }
    
    public int[] solution(int n, int[] info) {
        int[] answer = {};
        shot(new int[11], 0, 0, n, info);
        
        if(scoreMap.size()==1 && scoreMap.containsKey(-1)){
            answer = new int[1];
            answer[0] = -1;
            return answer;
        } 
        Object[] key = scoreMap.keySet().toArray();
        Arrays.sort(key);
        answer = scoreMap.get(key[key.length-1]);
        return answer;
    }
}
```