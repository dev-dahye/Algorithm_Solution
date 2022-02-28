# 프로그래머스 Level1 : 정렬 K번째수

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42748)

```java
import java.util.ArrayList;
import java.util.Collections;

class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int l = commands.length;
        int[] answer = new int[l];
        ArrayList<Integer> subArray = new ArrayList<Integer>();
        
        for(int n=0; n<l; n++){
            int i = commands[n][0];
            int j = commands[n][1];
            int k = commands[n][2];
            
            // i~j 배열 자르기
            for(int m=i-1; m<j; m++){
                subArray.add(array[m]);
            }
            
            // 정렬
            Collections.sort(subArray);

            // k번째 수    
            answer[n] = subArray.get(k-1);
            subArray.clear();
        }
  
        return answer;
    }
}
```