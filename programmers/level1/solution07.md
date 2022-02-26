# 프로그래머스 Level1 : 2019 카카오 개발자 겨울 인턴십 크레인 인형뽑기 게임


- [문제](https://programmers.co.kr/learn/courses/30/lessons/64061?language=java)

```java
import java.util.ArrayList;
class Solution {
    // 가장 위의 인형과 바로 아래의 인형을 터뜨릴수 있는지 확인하는 메서드
    public boolean canDollsPop(ArrayList<Integer> basket){
        boolean pop = false;
        if(basket.size()!=1){
            int recent = basket.get(basket.size()-1);
            int bottom = basket.get(basket.size()-2);
            pop = (recent==bottom);
        }   
        return pop;
    }
    
    public int solution(int[][] board, int[] moves) {
        int answer = 0;
        ArrayList<Integer> basket = new ArrayList<>();
        int size = board.length;
        
        // 움직인 크레인 위치에 인형의 유무확인     
        for(int move : moves){ 
            for(int i=0; i<size; i++){
                if(board[i][move-1] != 0){
                    // board에서 인형제거, basket에 인형추가
                    basket.add(board[i][move-1]);
                    board[i][move-1] = 0;
                    
                    // 추가된 인형과 아래 인형 터뜨리기 가능한지 확인
                    if(canDollsPop(basket)){
                        //인형 두개 터뜨리기
                        basket.remove(basket.size()-1);
                        basket.remove(basket.size()-1);
                        
                        answer+=2;        
                    }                        
                    break;
                } else {
                    continue;
                }
                
            }            
        }
        return answer;
    }
}
```