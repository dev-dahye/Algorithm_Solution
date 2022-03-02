# 프로그래머스 Level1 : 연습문제 정수 내림차순으로 배치하기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12933)

```java
import java.util.ArrayList;
import java.util.Collections;
class Solution {
    public long solution(long n) {
        long answer = 0;
        ArrayList<Long> nums = new ArrayList<>();
        StringBuilder sb = new StringBuilder();
        
        while(n!=0){
            nums.add(n%10);
            n/=10;
        }
        Collections.sort(nums);
        Collections.reverse(nums);
        
        for(long num: nums){
            answer = answer*10 + num;
        }
        
        return answer;
    }
}
```