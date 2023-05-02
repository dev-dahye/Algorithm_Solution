# 프로그래머스 Level2 : 티셔츠

- [문제](https://school.programmers.co.kr/tryouts/78117/challenges)

```java
import java.util.*;
class Solution {
    public int solution(int[] people, int[] tshirts) {
        Arrays.sort(people);
        Arrays.sort(tshirts);
        int answer = 0;
        for(int i=0, j=0; i<people.length && j<tshirts.length;){
            if(people[i]<=tshirts[j]){
                answer++;
                i++;
                j++;
            } else {
                j++;
            }
        }
        return answer;
    }
}
```