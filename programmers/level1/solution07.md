# 프로그래머스 Level1 : 2019 카카오 개발자 겨울 인턴십 크레인 인형뽑기 게임


- [문제](https://programmers.co.kr/learn/courses/30/lessons/64061?language=java)

## ArrayList

```java
import java.util.ArrayList;
class Solution {    
    public int solution(int[][] board, int[] moves) {
        int answer = 0;
        ArrayList<Integer> basket = new ArrayList<>();
        int size = board.length;
        
        // 움직인 크레인 위치에 인형의 유무확인     
        for(int move : moves){ 
            for(int i=0; i<size; i++){
                if(board[i][move-1] != 0){
                    // board에서 인형제거, basket에 인형추가
                    if(basket.size()!=0 && basket.get(basket.size()-1)==board[i][move-1]){
                        basket.remove(basket.size()-1);
                        answer+=2;
                    } else {
                        basket.add(board[i][move-1]);
                    }
                    board[i][move-1] = 0;
                    break;
                }
                
            }            
        }
        return answer;
    }
}
```
## Stack

```java
import java.util.Stack;

class Solution {   
    public int solution(int[][] board, int[] moves) {
        int answer = 0;
        Stack<Integer> basket = new Stack<>();
        int size = board.length;
        
        // 움직인 크레인 위치에 인형의 유무확인     
        for(int move : moves){ 
            for(int i=0; i<size; i++){
                if(board[i][move-1] != 0){
                    // board에서 인형제거, basket에 인형추가
                    if(!basket.isEmpty() && basket.peek() == board[i][move-1]){
                        System.out.println(basket.peek());
                        basket.pop();
                        answer+=2;        
                    } else{
                        basket.push(board[i][move-1]);
                    }
                    board[i][move-1] = 0;
                    break;
                }                 
                
            }            
        }
        return answer;
    }
}
```

## ArrayList와 Stack 수행시간

|테스트|ArrayList와|Stack|
|---|---|---|
테스트 1 〉	    통과 (0.04ms, 74.2MB       통과 (0.34ms, 78.5MB)    
테스트 2 〉	    통과 (0.04ms, 78MB)        통과 (0.42ms, 75.4MB)    
테스트 3 〉	    통과 (0.04ms, 75MB)        통과 (0.36ms, 79MB)      
테스트 4 〉	    통과 (0.60ms, 75.3MB)      통과 (1.09ms, 75.3MB)    
테스트 5 〉	    통과 (0.04ms, 79.3MB)      통과 (0.26ms, 78.8MB)    
테스트 6 〉	    통과 (0.06ms, 75.6MB)      통과 (0.33ms, 78.5MB)    
테스트 7 〉	    통과 (0.09ms, 77.2MB)      통과 (0.67ms, 73.9MB)    
테스트 8 〉	    통과 (0.38ms, 79MB)        통과 (1.54ms, 77.1MB)    
테스트 9 〉	    통과 (0.21ms, 78MB)        통과 (1.43ms, 76.7MB)    
테스트 10 〉	통과 (0.26ms, 77.5MB)      통과 (1.72ms, 77.4MB)    
테스트 11 〉	통과 (0.41ms, 77MB)        통과 (2.15ms, 74.2MB)    

>ArrayList
내부적으로 데이터를 배열에서 관리하며 데이터의 추가, 삭제를 위해서 임시 배열을 생성해 데이터를 복사하는 방법을 사용한다.
대량의 자료를 추가/삭제 하는 경우 그만큼 데이터의 복사가 많이 일어나게 되어 성능 저하가 발생
**이 문제에서는 마지막 데이터만 삭제하기 때문에 데이터 복사가 안 일어나 Stack보다 빠른 수행시간을 갖는 것** 

<br>
<br>

- - -
## Reference
- <https://woovictory.github.io/2018/12/27/DataStructure-Diff-of-Array-LinkedList/>
- <https://github.com/jki503/Algorithm_Solution/blob/main/programmers/level1/solution08.md>