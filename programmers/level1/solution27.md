# 프로그래머스 Level1 : 연습문제 같은 숫자는 싫어

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12906)

```java
import java.util.ArrayList;

public class Solution {
    public int[] solution(int[] arr) {
        int[] answer = {};        
        ArrayList<Integer> nums = new ArrayList<>();
        
        for(int num : arr){
            if(nums.isEmpty() || nums.get(nums.size()-1) != num){
                nums.add(num);   
            }
        }
        
        answer = new int[nums.size()];
        int size = 0;
        for(int num : nums){
            answer[size++] = num;
        }

        return answer;
    }
}
```