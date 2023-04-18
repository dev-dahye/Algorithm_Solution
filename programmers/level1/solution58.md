# 프로그래머스 Level1 : 바탕화면 정리

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/161990)

```java
class Solution {
    public int[] solution(String[] wallpaper) {
        int height = wallpaper.length;
        int width = wallpaper[0].length();
        int lux = 0, luy = width, rdx = height, rdy = 0;
        boolean xCheck = false;
        for(int x=0; x<height; x++){
            for(int y=0; y<width; y++){
                char state = wallpaper[x].charAt(y);
                if(state == '#'){
                    if(!xCheck){
                        lux = x;
                        xCheck=true;
                    } else{
                        rdx = x+1;
                    }
                    
                    if(luy>y){
                        luy = y;
                    }
                    if(rdy<y+1){
                        rdy = y+1;
                    }
                }
            }
        }
        int[] answer = {lux,luy,rdx,rdy};
        return answer;
    }
}
```

```java
class Solution {
    public int[] solution(String[] wallpaper) {
        int height = wallpaper.length;
        int width = wallpaper[0].length();
        int maxX = 0;
        int maxY = 0;
        int minX = 51;
        int minY = 51;
        
        for(int x=0; x<height; x++){
            for(int y=0; y<width; y++){
                char state = wallpaper[x].charAt(y);
                if(state == '#'){
                    maxX = Math.max(maxX,x);
                    maxY = Math.max(maxY,y);
                    minX = Math.min(minX,x);
                    minY = Math.min(minY,y);
                }
            }
        }
        int[] answer = {minX,minY,maxX+1,maxY+1};
        return answer;
    }
}
```