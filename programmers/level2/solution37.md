# 프로그래머스 Level2 : 위클리 챌린지 피로도

- [문제](https://programmers.co.kr/learn/courses/30/lessons/87946)

```java
class Solution {
    int answer = 0;
    int len = 0;
    boolean[] isVisited;
    void dfs(int k, int cnt, int[][] dungeons){
        if(k<=0) return;
        answer = Math.max(answer,cnt);
        for(int i=0; i<len; i++){
            if(!isVisited[i] && dungeons[i][0]<=k){
                isVisited[i] = true;
                dfs(k-dungeons[i][1], cnt+1, dungeons);
                isVisited[i] = false;
            }
        }
    }
    public int solution(int k, int[][] dungeons) {
        len = dungeons.length;
        isVisited = new boolean[len];
            
        dfs(k,0,dungeons);
        return answer;
    }
}
```