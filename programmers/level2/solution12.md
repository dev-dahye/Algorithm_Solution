# 프로그래머스 Level2 : 깊이/너비 우선 탐색(DFS/BFS) 타겟 넘버

- [문제](https://programmers.co.kr/learn/courses/30/lessons/43165)

```java
class Solution {
    int answer = 0;
    void dfs(int num, int index, int sign, int[] numbers, int target){
        int sum = num + numbers[index]*sign;
        if(index==numbers.length-1){
            if(sum == target){
                answer++;
                return;
            }
        } else{
            dfs(sum,index+1,1,numbers,target);
            dfs(sum,index+1,-1,numbers,target);
        }
        return;
    }
    
    public int solution(int[] numbers, int target) {
        dfs(0,0,1,numbers,target);
        dfs(0,0,-1,numbers,target);
        
        return answer;
    }
}
```