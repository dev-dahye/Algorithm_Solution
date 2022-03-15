# 프로그래머스 Level2 : Summer/Winter Coding(~2018) 방문 길이

- [문제](https://programmers.co.kr/learn/courses/30/lessons/49994)

```java
import java.util.HashSet;
import java.util.Iterator;
class Solution {
    final int MAP_SIZE = 5;
    public int solution(String dirs) {
        HashSet<String> set = new HashSet<>();

        int currR = 0;
        int currC = 0;
        
        for(char c : dirs.toCharArray()){
            if(currR >= MAP_SIZE && c=='U') continue;
            else if(currR <= MAP_SIZE*-1 && c=='D') continue;
            else if(currC >= MAP_SIZE && c=='R') continue;
            else if(currC <= MAP_SIZE*-1 && c=='L') continue;
            
            StringBuilder sb1 = new StringBuilder();
            sb1.append(currR);
            sb1.append(" ");
            sb1.append(currC);
            sb1.append(" ");
            sb1.append(c);
            
            set.add(sb1.toString());
            
            String reverse = "";
            if(c=='U'){
                currR+=1;
                reverse = " D";
            } else if(c=='D'){
                currR-=1;
                reverse = " U";
            } else if(c=='R'){
                currC+=1;
                reverse = " L";
            } else {
                currC-=1;   
                reverse = " R";
            }
            
            StringBuilder sb2 = new StringBuilder();
            sb2.append(currR);
            sb2.append(" ");
            sb2.append(currC);
            sb2.append(reverse);
            
            set.add(sb2.toString());
            
        }
       
        return set.size()/2;
    }
}
```