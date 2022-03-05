# 프로그래머스 Level2 : 스택/큐 기능개발

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42586)

```java
import java.util.Queue;
import java.util.LinkedList;
import java.util.ArrayList;
import java.util.Arrays;

class Solution {
    public int[] solution(int[] progresses, int[] speeds) {
        int[] answer = {};
        int l = progresses.length;
        Queue<Integer> complete = new LinkedList<>();
        ArrayList<Integer> publishCnt = new ArrayList<>();
        
        boolean[] isComplete = new boolean[l];
        int cnt = 0;
        int wholeCnt = 0;
        
        int order = 0;
        while(wholeCnt<l){
            // 하루 진행률 올리기
            for(int j=0; j<l; j++){
                if(!isComplete[j]) progresses[j] += speeds[j];    
            }

            // 끝난 작업을 큐에 저장 
            for(int j=0; j<l; j++){
                if(!isComplete[j] && progresses[j]>=100){
                    isComplete[j] = true;
                    complete.offer(j);
                }
            }
            
            if(isComplete[order]){        
                int s = complete.size();
                for(int i=0; i<s; i++){
                    int p =complete.poll();
                    for(int k=p; k>=0; k--){
                        if(!isComplete[k]){
                            complete.offer(p);
                            break;
                        }
                    }
                }
                cnt = s - complete.size();
                wholeCnt+=cnt;
                if(cnt!=0) publishCnt.add(cnt);
                cnt = 0;
                
                
                order++;
            }
                
        }
        
        answer = new int[publishCnt.size()];
        int index = 0;
        for(int c : publishCnt){
            answer[index++] = c;
        }
        
        return answer;
    }
}
```