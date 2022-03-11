# 프로그래머스 Level2 : 스택/큐 주식가격

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42584#)

## Stack
```java
import java.util.Stack;
class Solution {
    public int[] solution(int[] prices) {
        int[] answer = new int[prices.length];
        Stack<Integer[]> stack = new Stack<>();
        
        for(int i=0;i<prices.length;i++){
            Integer[] tmp = {prices[i],i};
            if(stack.empty()){
                stack.push(tmp);
                continue;
            } else{
                while(stack.peek()[0]>prices[i]){
                    answer[stack.peek()[1]]=i-stack.peek()[1];
                    stack.pop();
                    
                    if(stack.empty())
                        break;
                }
            }
            
            stack.push(tmp);
        }
        
        while(!stack.empty()){
            answer[stack.peek()[1]]=prices.length-1-stack.peek()[1];
            stack.pop();
        }
        
        return answer;
    }
}
```

## for 문
```java
class Solution {
    public int[] solution(int[] prices) {
        int[] answer = new int[prices.length];
        
        for(int i=0; i<prices.length-1; i++){
            for(int j=i+1; j<prices.length; j++){
                if(prices[i]<=prices[j]){
                    answer[i]++;   
                } else{
                    answer[i]++;   
                    break;
                }
            }
        }

        return answer;
    }
}
```

## Stack / for문 수행시간 차이
  
|테스트|Stack|for문|
|---|---|---|
|정확성  테스트|||
|테스트 1 〉	|통과 (0.11ms, 75MB)     |통과 (0.03ms, 73.3MB)    |
|테스트 2 〉	|통과 (0.59ms, 66.5MB)   |통과 (0.02ms, 76MB)      |
|테스트 3 〉	|통과 (1.55ms, 77.6MB)   |통과 (0.21ms, 77.6MB)    |
|테스트 4 〉	|통과 (1.60ms, 90MB)     |통과 (0.20ms, 68.9MB)    |
|테스트 5 〉	|통과 (1.75ms, 81.9MB)   |통과 (0.20ms, 79.3MB)    |
|테스트 6 〉	|통과 (0.32ms, 80MB)     |통과 (0.02ms, 76.7MB)    |
|테스트 7 〉	|통과 (1.22ms, 71.9MB)   |통과 (0.09ms, 75.1MB)    |
|테스트 8 〉	|통과 (1.02ms, 80.7MB)   |통과 (0.11ms, 75MB)      |
|테스트 9 〉	|통과 (0.34ms, 66.7MB)   |통과 (0.02ms, 71.3MB)    |
|테스트 10 〉   |통과 (1.31ms, 76MB)     |통과 (0.33ms, 81.1MB)    |
|효율성  테스트 |||
|테스트 1 〉	|통과 (46.79ms, 74.3MB)  |통과 (21.87ms, 67.4MB) |
|테스트 2 〉	|통과 (43.54ms, 71.8MB)  |통과 (15.03ms, 63.5MB) |
|테스트 3 〉	|통과 (81.09ms, 74.4MB)  |통과 (18.41ms, 73.8MB) |
|테스트 4 〉	|통과 (44.37ms, 74.9MB)  |통과 (19.03ms, 70MB)   |
|테스트 5 〉	|통과 (44.14ms, 70.5MB)  |통과 (12.68ms, 77.4MB) |