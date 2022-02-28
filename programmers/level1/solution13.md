# 프로그래머스 Level1 : 탐욕법(Greedy) 체육복

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42862#)

```java
class Solution {
    public int solution(int n, int[] lost, int[] reserve) {
        int answer = 0;
        int[] students = new int[n];
        
        for(int i=0; i<n; i++){
            students[i] = 1;
        }
        
        for(int r: reserve){
            students[r-1]++;
        }
        
        for(int l :lost){
            students[l-1]--;
        }
            
        for(int i=0; i<n; i++){
            if(students[i]==0){
                if(i-1>=0 && students[i-1]==2){
                    students[i] = 1;
                    students[i-1] = 1;
                    continue;
                }
                if(i+1<n && students[i+1]==2){
                    students[i] = 1;
                    students[i+1] = 1;
                }
            }
        }
        
        for(int i=0; i<n; i++){
            if(students[i]>=1){
                answer++;
            }
        }
        
        return answer;
    }
}
```