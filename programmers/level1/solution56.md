# 프로그래머스 Level1 : 추억 점수

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/176963)

```java
import java.util.HashMap;
class Solution {
    public int[] solution(String[] name, int[] yearning, String[][] photo) {
        HashMap<String,Integer> yearningMap = new HashMap<String,Integer>();
        for(int i=0; i<name.length; i++){
            yearningMap.put(name[i],yearning[i]);
        }
        int[] answer = new int[photo.length];
        for(int i=0; i<photo.length; i++){
            int sum = 0;
            for(int j=0; j<photo[i].length; j++){
                sum += yearningMap.get(photo[i][j])==null?0:yearningMap.get(photo[i][j]);
                
            }
            answer[i] = sum;
        }
        
        return answer;
    }
}
```