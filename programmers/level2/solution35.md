# 프로그래머스 Level2 :  완전탐색 카펫

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42842)

```java
class Solution {
    int h;
    int v;
    void findCarpetSize(int carpet, int brown, int yellow){
        for(int i=3; i<=Math.sqrt(carpet); i++){
            if(carpet%i==0){
                if((i-2)*((carpet/i)-2) == yellow){
                    h = carpet/i;
                    v = i;
                }
            }
        }
    }
    public int[] solution(int brown, int yellow) {
        int[] answer = new int[2];
        findCarpetSize(brown+yellow, brown, yellow);
        answer[0] = h;
        answer[1] = v;
        return answer;
    }
}
```