# 프로그래머스 Level1 : 가장 가까운 같은 글자

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/142086)

```java
class Solution {
    public int[] solution(String s) {
        int l = s.length();
        int[] answer = new int[l];
        for(int i=l-1; i>=0; i--){
            answer[i] = -1;
            for(int j=i-1; j>=0; j--){
                if(s.charAt(i)==s.charAt(j)){
                    answer[i] = i-j;
                    break;
                }  
            }
        }
        
        return answer;
    }
}
```
```java
import java.util.HashMap;
class Solution {
    public int[] solution(String s) {
        HashMap<Character,Integer> hashMap = new HashMap<Character,Integer>();
        int[] answer = new int[s.length()];
        for(int i=0; i<s.length(); i++){
            int n = hashMap.getOrDefault(s.charAt(i),-1);
            answer[i] = n==-1?-1:i-n;
            hashMap.put(s.charAt(i),i);
        }
        
        return answer;
    }
}
```