# 프로그래머스 Level1 : 2021 Dev-Matching: 웹 백엔드 개발자(상반기) 로또의 최고 순위와 최저 순위
- [문제](https://programmers.co.kr/learn/courses/30/lessons/77484?language=java)

```java
class Solution {
    public int[] solution(int[] lottos, int[] win_nums) {
        int[] answer = new int[2];
        
        int zeroCnt = 0;
        int corrCnt = 0;
        for(int lotto : lottos){
            if(lotto==0){
                zeroCnt++;
            }
            for(int win_num:win_nums){
                if(win_num == lotto){
                    corrCnt++;
                    break;
                }
            }
        }
        
        answer[0] = 6-(corrCnt+zeroCnt)+1<=6?6-(corrCnt+zeroCnt)+1:6;
        answer[1] = (6-corrCnt+1)<=6?6-corrCnt+1:6;
        
        return answer;
    }
}
```