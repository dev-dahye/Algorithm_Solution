# 프로그래머스 Level2 : 연습문제 최댓값과 최솟값

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12939)

```java
import java.util.Arrays;
class Solution {
    public String solution(String s) {
        String answer = "";
        String[] strNumbers = s.split(" ");
        int len = strNumbers.length;
        
        int[] numbers = new int[len];
        for(int i=0; i<len; i++){
            numbers[i] = Integer.parseInt(strNumbers[i]);
        }
        
        Arrays.sort(numbers);
        answer+=numbers[0]+" ";
        answer+=numbers[len-1];
        return answer;
    }
}
```