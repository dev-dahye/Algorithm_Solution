# 프로그래머스 Level1 : 2018 KAKAO BLIND RECRUITMENT [1차] 다트 게임

- [문제](https://programmers.co.kr/learn/courses/30/lessons/17682)

```java
class Solution {
    public int solution(String dartResult) {
        int answer = 0;
        int[] scores = new int[3];
        int l = dartResult.length();
        
        int index = -1;
        for(int i=0; i<l; i++){
            char c = dartResult.charAt(i);
            if(c>='0' && c<='9'){
                if(c=='1' && dartResult.charAt(i+1)=='0'){
                    index++;
                    scores[index] = 10;
                    i++;
                } else{
                    index++;
                    scores[index] = c-'1'+1;
                }
            } else if(c=='D'){
                scores[index] = (int)Math.pow(scores[index],2);
            } else if(c=='T'){
                scores[index] = (int)Math.pow(scores[index],3);
            } else if(c=='*'){
                scores[index] *= 2;
                if(index-1>=0){
                    scores[index-1] *= 2;
                }
            } else if(c=='#'){
                scores[index] *= -1;
            }
        }
        
        for(int score: scores){
            answer+=score;
        }
        
        return answer;
    }
}
```