# 프로그래머스 Level2 : 2021 카카오 채용연계형 인턴십 거리두기 확인하기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/81302)

```java
class Solution {
    public int[] solution(String[][] places) {
        int[] answer = new int[5];
        // 맨헤튼거리 2이하의 좌표 : 상1상2 하1하2 좌1좌2 우1우2 상좌 상우 하좌 하우
        int[] dirR = {-1,-2,1,2,0,0,0,0,-1,-1,1,1};
        int[] dirC = {0,0,0,0,-1,-2,1,2,-1,1,-1,1};
        
        int index=0;
        for(String[] p : places){
            char[][] place = new char[5][5];
            for(int i=0; i<5; i++){
                for(int j=0; j<5; j++){
                    place[i][j] = p[i].charAt(j);
                }
            }
            
            int row = 0;
            label: while(row<5){
                for(int col=0; col<5; col++){
                    // 사람사이의 맨해튼거리가 2초과인지
                    if(place[row][col]=='P'){
                        for(int d=0; d<12; d++){
                            int r = row+dirR[d];
                            int c = col+dirC[d];
                            if(r>=0&&r<5 && c>=0&&c<5 && place[r][c]=='P'){
                                if(d==0||d==2||d==4||d==6){// 맨해튼거리=1 : 사이에 파티션이 있을수 없음
                                    answer[index] = 0;
                                    break label;
                                
                                }else if(d==1||d==3||d==5||d==7){//맨해튼거리=2:사이에 파티션이있는지 확인
                                    if(place[row+(dirR[d]/2)][col+(dirC[d]/2)] != 'X'){
                                        answer[index] = 0;
                                        break label;
                                    }
                                }else{ // 대각선의 경우 파티션이 두개
                                    //상좌 상우
                                    if(d==8 || d==9){
                                        int rr = row+dirR[0];
                                        int cc = col+dirC[0];
                                        if(rr>=0&&rr<5&&cc>=0&&cc<5&&place[rr][cc] != 'X'){
                                            answer[index] = 0;
                                            break label;
                                        }
                                        if(d==8){
                                            rr = row+dirR[4];
                                            cc = col+dirC[4];
                                            if(rr>=0&&rr<5&&cc>=0&&cc<5&&place[rr][cc] != 'X'){
                                                answer[index] = 0;
                                                break label;
                                            }
                                        } else{
                                            rr = row+dirR[6];
                                            cc = col+dirC[6];
                                            if(rr>=0&&rr<5&&cc>=0&&cc<5&&place[rr][cc] != 'X'){
                                                answer[index] = 0;
                                                break label;
                                            }
                                        }
                                    }
                                    //하좌 하우
                                    if(d==10 || d==11){
                                        int rr = row+dirR[2];
                                        int cc = col+dirC[2];
                                        if(rr>=0&&rr<5&&cc>=0&&cc<5&&place[rr][cc] != 'X'){
                                            answer[index] = 0;
                                            break label;
                                        }
                                        if(d==10){
                                            rr = row+dirR[4];
                                            cc = col+dirC[4];
                                            if(rr>=0&&rr<5&&cc>=0&&cc<5&&place[rr][cc] != 'X'){
                                                answer[index] = 0;
                                                break label;
                                            }
                                        } else{
                                            rr = row+dirR[6];
                                            cc = col+dirC[6];
                                            if(rr>=0&&rr<5&&cc>=0&&cc<5&&place[rr][cc] != 'X'){
                                                answer[index] = 0;
                                                break label;
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }
                }
                answer[index] = 1;
                row++;
            }
            index++;
        }
        
        
        return answer;
    }
}
```