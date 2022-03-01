# 프로그래머스 Level1 : 연습문제 나누어 떨어지는 숫자 배열

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12910)

```java
import java.util.Arrays;
import java.util.ArrayList;
class Solution {
    public int[] solution(int[] arr, int divisor) {
        int[] answer = {};
        ArrayList<Integer> nums = new ArrayList<>();
        
        for(int n : arr){
            if(n%divisor == 0){
                nums.add(n);
            }
        }
        
        if(nums.size()==0){
            answer = new int[]{-1};
        } else{
            answer = new int[nums.size()];
            int size = 0;
            for(int num: nums){
                answer[size++] = num;
            }
            Arrays.sort(answer);
        }
        return answer;
    }
}
```