# 프로그래머스 Level1 : 연습문제 자연수 뒤집어 배열로 만들기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12932)

```java
import java.util.ArrayList;
class Solution {
    public int[] solution(long n) {
        int[] answer = {};
        ArrayList<Long> nums = new ArrayList<>();
        
        while(n!=0){
            nums.add(n%10);
            n/=10;
        }
        
        answer = new int[nums.size()];
        int index = 0;
        for(long num: nums){
            answer[index++] = (int)num;
        }
        
        return answer;
    }
}
```