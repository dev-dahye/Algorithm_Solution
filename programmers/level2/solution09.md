# 프로그래머스 Level2 : 연습문제 124 나라의 숫자

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12899#)

### StringBuilder
```java
class Solution {
    private StringBuilder digit(int num){
        StringBuilder sb = new StringBuilder();
        if(num%3==1) sb.insert(0,"1");
        else if (num%3==2) sb.insert(0,"2");
        else{
            num--;
            sb.insert(0,"4");
        }
        
        if(num>3) sb.insert(0,digit(num/3));
        
        return sb;
    }
    
    public String solution(int n) {
        String answer = digit(n).toString();
  
        return answer;
    }
}
```

### Stack
```java
import java.util.Stack;
class Solution {
    Stack<Integer> stack = new Stack<>();
    
    private void digit(int num){
        if(num%3==1) stack.push(1);
        else if (num%3==2) stack.push(2);
        else{
            num--;
            stack.push(4);
        }
        
        if(num>3) digit(num/3);
    }
    
    public String solution(int n) {
        String answer = "";
        
        digit(n);
        while(!stack.isEmpty()){
            answer+= stack.pop();    
        }
        return answer;
    }
}
```


정확성 테스트
|#|StringBuilder|Stack|
|---|---|---|
|테스트 1 〉	|통과 (0.04ms, 73MB)    |통과 (1.79ms, 73.3MB)|
|테스트 2 〉	|통과 (0.04ms, 77.1MB)  |통과 (1.78ms, 78.5MB)|
|테스트 3 〉	|통과 (0.06ms, 84.6MB)  |통과 (1.26ms, 73.5MB)|
|테스트 4 〉	|통과 (0.05ms, 73.6MB)  |통과 (1.26ms, 70.4MB)|
|테스트 5 〉	|통과 (0.05ms, 73.9MB)  |통과 (1.48ms, 79.8MB)|
|테스트 6 〉	|통과 (0.05ms, 81.7MB)  |통과 (1.95ms, 83.6MB)|
|테스트 7 〉	|통과 (0.05ms, 73.9MB)  |통과 (1.27ms, 78.7MB)|
|테스트 8 〉	|통과 (0.05ms, 74MB)    |통과 (1.44ms, 76.3MB)|
|테스트 9 〉	|통과 (0.05ms, 74.8MB)  |통과 (1.68ms, 65.6MB)|
|테스트 10 〉	|통과 (0.06ms, 76.2MB)	|통과 (1.36ms, 76MB)  |
|테스트 11 〉	|통과 (0.06ms, 69.2MB)	|통과 (1.35ms, 77.7MB)|
|테스트 12 〉	|통과 (0.06ms, 67.6MB)	|통과 (1.67ms, 71.8MB)|
|테스트 13 〉	|통과 (0.06ms, 74.1MB)	|통과 (1.26ms, 72.6MB)|
|테스트 14 〉	|통과 (0.09ms, 74.3MB)	|통과 (1.17ms, 77.4MB)|

효율성 테스트 
|#|StringBuilder|Stack|
|---|---|---| 
|테스트 1 〉    |통과 (0.11ms, 52.5MB)  |통과 (1.69ms, 52.5MB)|
|테스트 2 〉    |통과 (0.12ms, 52.3MB)  |통과 (1.55ms, 53.2MB)|
|테스트 3 〉    |통과 (0.14ms, 53.2MB)  |통과 (1.68ms, 52.8MB)|
|테스트 4 〉    |통과 (0.11ms, 52.4MB)  |통과 (1.89ms, 51.6MB)|
|테스트 5 〉    |통과 (0.10ms, 53MB)    |통과 (1.40ms, 52.4MB)|
|테스트 6 〉    |통과 (0.14ms, 52.3MB)  |통과 (1.64ms, 52.4MB)|