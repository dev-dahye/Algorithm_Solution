# 프로그래머스 Level2 : Summer/Winter Coding(~2018) 영어 끝말잇기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12981)

```java
import java.util.HashSet;
class Solution {
    public int[] solution(int n, String[] words) {
        int[] answer = new int[2];
        HashSet<String> wordSet = new HashSet<>();

        int person =0;
        int cnt = 0;
        char start = words[0].charAt(0);
        for(String word : words){
            if(!wordSet.add(word) || word.charAt(0)!=start){
                answer[0] = person + 1;
                answer[1] = cnt/n + 1;
                break;
            }
            start = word.charAt(word.length()-1);
            person = (person+1)%n;
            cnt++;
            
        }
        return answer;
    }
}
```