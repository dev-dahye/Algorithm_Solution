# 프로그래머스 Level1 : 월간 코드 챌린지 시즌1 두 개 뽑아서 더하기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/68644)

```java
import java.util.HashSet;
import java.util.ArrayList;
import java.util.Collections;
class Solution {
    public int[] solution(int[] numbers) {
        int[] answer = {};
        int l = numbers.length;
        HashSet<Integer> addNums = new HashSet<>();
        
        for(int i=0; i<l-1; i++){
            for(int j=i+1; j<l; j++){
                addNums.add(numbers[i]+numbers[j]);
            }
        }
        
        ArrayList<Integer> sortedList = new ArrayList<>(addNums);
        Collections.sort(sortedList);
        
        int s = sortedList.size();
        answer = new int[s];
        for(int i=0; i<s; i++){
            answer[i] = sortedList.get(i);
        }
        
        return answer;
    }
}
```