# 프로그래머스 Level2 : 완전탐색 소수 찾기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42839)

```java
import java.util.HashSet;
class Solution {
    int cnt =0;
    boolean[] isVisited;
    HashSet<Integer> numSet = new HashSet<>();
    
    void dfs(String num,String numbers){
        boolean isPrime = true;
        if(!num.equals("")){
            int numInt = Integer.parseInt(num);
            if(numInt!=1 && numInt!=0){
                if(numSet.add(numInt)){
                    for(int i=2; i<=Math.sqrt(numInt); i++){
                        if(numInt%i==0){
                            isPrime = false;
                            break;
                        }
                        isPrime = true;
                    }
                    if(isPrime){
                        cnt++;
                    }
                }
            }
            
        }
        
        for(int i=0; i<isVisited.length; i++){
            if(!isVisited[i]){
                isVisited[i]=true;
                dfs(num+numbers.charAt(i),numbers);
                isVisited[i]=false;

            }
        }
    }
    public int solution(String numbers) {
        isVisited = new boolean[numbers.length()];
        dfs("",numbers);
       
        return cnt;
    }
}
```