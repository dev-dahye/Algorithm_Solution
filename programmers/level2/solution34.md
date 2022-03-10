# 프로그래머스 Level2 : 정렬 H-Index

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42747#)

```java
import java.util.Collections;
import java.util.ArrayList;
class Solution {
    public int solution(int[] citations) {
        int answer = 0;
        ArrayList<Integer> list = new ArrayList<>();
        for(int c : citations){
            list.add(c);
        }
        Collections.sort(list,Collections.reverseOrder());
        int size = list.size();
        int h = list.get(0);
        int cnt = 0;
        
        while(true){
            cnt = 0;
            for(int i=0; i<size; i++){
                if(list.get(i)>=h){
                    cnt++;
                    continue;
                }
                break;
            }
            
            if(h>cnt){
                h--;
            } else if(h<=cnt){
                break;
            }
        }
    
        return h;
    }
}
```