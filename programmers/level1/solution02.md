# 프로그래머스 Level1 : 2020 카카오 인턴십 키패드 누르기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/67256?language=java)

```java
 public String solution(int[] numbers, String hand) {
        //위치 : 0,1,2,3,4,5,6,7,8,9
        int dirX[] = {3,0,0,0,1,1,1,2,2,2};
        int dirY[] = {1,0,1,2,0,1,2,0,1,2};
        String answer = "";
        Hand left = new Hand(3, 0);
        Hand right = new Hand(3, 2);
        int distanceLeft;
        int distanceRight;
        
        for(int num : numbers){
            // 번호 확인, 확실한 것 누르기
            if(num == 1 || num == 4 || num == 7){
                answer+="L";
                left.x = dirX[num];
                left.y = dirY[num];
            } else if(num == 3 || num == 6 || num == 9){
                answer+="R";
                right.x = dirX[num];
                right.y = dirY[num];
            } else{
                // 어떤 손가락이 가까운지        
                distanceLeft = Math.abs(left.x-dirX[num])+Math.abs(left.y-dirY[num]);
                distanceRight = Math.abs(right.x-dirX[num])+Math.abs(right.y-dirY[num]);
                if(distanceLeft>distanceRight){
                    answer+="R";
                    right.x = dirX[num];
                    right.y = dirY[num];
                }
                else if(distanceLeft<distanceRight){
                    answer+="L";
                    left.x = dirX[num];
                    left.y = dirY[num];
                }          
                else{
                    // 같을땐 어떤손잡이인지 확인
                    if(hand.equals("right")){
                        answer+="R";
                        right.x = dirX[num];
                        right.y = dirY[num];
                    }else{
                        answer+="L";
                        left.x = dirX[num];
                        left.y = dirY[num];
                    }
                }
                
            }
        }
        return answer;
    }
}
```