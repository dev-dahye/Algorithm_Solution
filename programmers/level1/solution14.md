# 프로그래머스 Level1 : 찾아라 프로그래밍 마에스터 폰켓몬


- [문제](https://programmers.co.kr/learn/courses/30/lessons/1845)

```java
import java.util.HashSet;
class Solution {
    public int solution(int[] nums) {
        int answer = 0;
        int cnt = nums.length/2;
        HashSet<Integer> set = new HashSet<>();
        
        for(int num : nums){
          if(set.add(num)){
              answer++;
          }
        }
        
        answer = answer>cnt? cnt : answer;

        return answer;
    }
}
```