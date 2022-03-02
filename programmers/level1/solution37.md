# 프로그래머스 Level1 : 연습문제 문자열을 정수로 바꾸기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12925)

#### Integer.parseInt 음수도 변환 가능 
```java
class Solution {
    public int solution(String s) {
        int answer = Integer.parseInt(s);
        
        return answer;
    }
}
```

```java
class Solution {
    public int solution(String s) {
        int answer = 0;
        if(s.charAt(0) == '-' || s.charAt(0) == '+'){
            answer = Integer.parseInt(s.substring(1));
            if(s.charAt(0) == '-'){
                answer*=-1;
            }
        } else{
            answer = Integer.parseInt(s);
        }
        
        return answer;
    }
}
```

<br>
<br>

- - -
## Reference
-<https://github.com/jki503/Algorithm_Solution/blob/main/programmers/level1/solution38.md>