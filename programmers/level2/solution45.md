# 프로그래머스 Level2 : 위클리 챌린지 모음사전

- [문제](https://programmers.co.kr/learn/courses/30/lessons/84512)

```java
class Solution {
    public int solution(String word) {
        int answer = 0;
        final int allCase = (int)(Math.pow(5,1)+Math.pow(5,2)+Math.pow(5,3)+Math.pow(5,4)+Math.pow(5,5));
        int len = word.length();
        for(int i=0; i<len; i++){
            char c = word.charAt(i);
            switch(c){
                case 'A': 
                    answer+=1;
                    break;
                case 'E': 
                    answer+= allCase/(int)Math.pow(5,i+1)+1;
                    break;
                case 'I': 
                    answer+= allCase/(int)Math.pow(5,i+1)*2+1;
                    break;
                case 'O': 
                    answer+= allCase/(int)Math.pow(5,i+1)*3+1;
                    break;
                case 'U': 
                    answer+= allCase/(int)Math.pow(5,i+1)*4+1;
                    break;
            }
        }
        
        return answer;
    }
}
```

<br>
<br>

- - -

## Reference
- <https://programmers.co.kr/questions/25140>