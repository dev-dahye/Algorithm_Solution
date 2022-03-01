# 프로그래머스 Level1 : 2019 KAKAO BLIND RECRUITMENT 실패율

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42889)

```java
class Solution {
    public int[] solution(int N, int[] stages) {
        int[] answer = new int[N];
        int userCnt = stages.length;
        int[] success = new int[N];
        double[] failure = new double[N];
        
        for(int stage : stages){         
            if(stage<=N)
                failure[stage-1]++;   
            for(int i=stage-2; i>=0; i--){
                if(i>=0){
                    success[i]++;
                }
            }
        }
        
        // 실패율
        failure[0] /= userCnt;
        for(int i=1; i<N; i++){
            if(success[i-1]!=0){
                failure[i] /= success[i-1];
            } else{
                failure[i] =0;
            }
            
        }
        
        int max = 0;
        for(int j=0; j<N; j++){
            for(int i=1; i<N; i++){
                if(failure[max]<failure[i]){
                    max = i;
                }
            }
            failure[max] = -1;
            answer[j] = max+1;
            max=0;
        }
        return answer;
    }
}
```