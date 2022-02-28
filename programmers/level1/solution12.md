# 프로그래머스 Level1 : 완전탐색 모의고사

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42840)

```java

class Solution {
    public int[] solution(int[] answers) {
        int[] answer = {};
        int[] s1 = {1,2,3,4,5};
        int[] s2 = {2,1,2,3,2,4,2,5};
        int[] s3 = {3,3,1,1,2,2,4,4,5,5};
        
        int[] corrCnt = new int[3];
        
        int max = -1;
        int max2 = -1;
        
        int index = 0;
        for(int a : answers){
            if(a==s1[(index%5)]){
                corrCnt[0]++;
            }
            if(a==s2[(index%8)]){
                corrCnt[1]++;
            }
            if(a==s3[(index%10)]){
                corrCnt[2]++;
            }
            index++;
        }
        
        if(corrCnt[0]==corrCnt[1] && corrCnt[0]==corrCnt[2]){
            return new int[]{1,2,3};
        } 
        
        max = 0;
        for(int i=1; i<3; i++){
            if(corrCnt[max]<corrCnt[i]){
                max = i;
                max2 = -1;
            } else if(corrCnt[max]==corrCnt[i]){
                max2 = i;
            }
        }
        
        if(max2 == -1){
            answer = new int[]{max+1};
        } else{
            answer = new int[]{max+1,max2+1};
        }
        return answer;
    }
}
```