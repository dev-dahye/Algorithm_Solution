# 프로그래머스 Level1 : 2020 카카오 인턴십 키패드 누르기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/67256?language=java)

```java
 class Solution {
    class Hand{
        int x;
        int y;
        
        public Hand(int x, int y){
            this.x = x;
            this.y = y;
        }
    }
        
    public String solution(int[] numbers, String hand) {
        //위치 : 0,1,2,3,4,5,6,7,8,9
        int dirX[] = {3,0,0,0,1,1,1,2,2,2};
        int dirY[] = {1,0,1,2,0,1,2,0,1,2};
        String answer = "";
        StringBuilder answerSb = new StringBuilder();
        
        Hand left = new Hand(3, 0);
        Hand right = new Hand(3, 2);
        int distanceLeft;
        int distanceRight;
        
        for(int num : numbers){
            // 번호 확인, 확실한 것 누르기
            if(num == 1 || num == 4 || num == 7){
                //answer+="L";
                answerSb.append("L");
                left.x = dirX[num];
                left.y = dirY[num];
            } else if(num == 3 || num == 6 || num == 9){
                //answer+="R";
                answerSb.append("R");
                right.x = dirX[num];
                right.y = dirY[num];
            } else{
                // 어떤 손가락이 가까운지        
                distanceLeft = Math.abs(left.x-dirX[num])+Math.abs(left.y-dirY[num]);
                distanceRight = Math.abs(right.x-dirX[num])+Math.abs(right.y-dirY[num]);
                if(distanceLeft>distanceRight){
                    //answer+="R";
                    answerSb.append("R");
                    right.x = dirX[num];
                    right.y = dirY[num];
                }
                else if(distanceLeft<distanceRight){
                    //answer+="L";
                    answerSb.append("L");
                    left.x = dirX[num];
                    left.y = dirY[num];
                }          
                else{
                    // 같을땐 어떤손잡이인지 확인
                    if(hand.equals("right")){
                        //answer+="R";
                        answerSb.append("R");
                        right.x = dirX[num];
                        right.y = dirY[num];
                    }else{
                        //answer+="L";
                        answerSb.append("L");
                        left.x = dirX[num];
                        left.y = dirY[num];
                    }
                }
                
            }
        }
        
        answer = answerSb.toString();
        return answer;
    }
}
```


## String `+`/ StringBuilder `append()` 연산시간 차이
  
|테스트|String `+`|StringBuilder `append()`|
|---|---|---|
|테스트 1 〉    |통과 (2.76ms, 73.4MB)   |통과 (0.18ms, 71.7MB) |
|테스트 2 〉    |통과 (3.08ms, 74.9MB)   |통과 (0.23ms, 75.2MB) |
|테스트 3 〉    |통과 (2.46ms, 71.5MB)   |통과 (0.20ms, 77.9MB) |
|테스트 4 〉    |통과 (2.56ms, 79.6MB)   |통과 (0.19ms, 74.4MB) |
|테스트 5 〉    |통과 (2.63ms, 71.5MB)   |통과 (0.20ms, 74.4MB) |
|테스트 6 〉    |통과 (2.70ms, 73.8MB)   |통과 (0.19ms, 74.7MB) |
|테스트 7 〉    |통과 (2.55ms, 74MB)     |통과 (0.21ms, 72.7MB) |
|테스트 8 〉    |통과 (2.62ms, 77.9MB)   |통과 (0.22ms, 75.4MB) |
|테스트 9 〉    |통과 (2.64ms, 66.3MB)   |통과 (0.34ms, 70.9MB) |
|테스트 10 〉   |통과 (2.22ms, 74.8MB)   |통과 (0.31ms, 72.4MB) |
|테스트 11 〉   |통과 (3.46ms, 77.3MB)   |통과 (0.23ms, 74.4MB) |
|테스트 12 〉   |통과 (2.48ms, 72.7MB)   |통과 (0.23ms, 73.7MB) |
|테스트 13 〉   |통과 (2.79ms, 73.9MB)   |통과 (0.22ms, 73.3MB) |
|테스트 14 〉   |통과 (2.91ms, 73.9MB)   |통과 (0.25ms, 76.2MB) |
|테스트 15 〉   |통과 (4.79ms, 77.3MB)   |통과 (0.46ms, 70.3MB) |
|테스트 16 〉   |통과 (2.83ms, 76.6MB)   |통과 (0.30ms, 78.4MB) |
|테스트 17 〉   |통과 (4.25ms, 75.8MB)   |통과 (0.45ms, 74MB)   |
|테스트 18 〉   |통과 (3.82ms, 79.2MB)   |통과 (0.45ms, 73MB)   |
|테스트 19 〉   |통과 (3.20ms, 76.2MB)   |통과 (0.40ms, 75.6MB) |
|테스트 20 〉   |통과 (3.55ms, 72.4MB)   |통과 (0.43ms, 77MB)   |


<br>
<br>

- - -

## Refernce
- <https://github.com/jki503/Algorithm_Solution/blob/main/programmers/level1/solution04.md>
- <https://hardlearner.tistory.com/288>