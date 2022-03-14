# 프로그래머스 Level2 : 위클리 챌린지 교점에 별 만들기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/87377)

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashSet;
import java.util.HashMap;
import java.util.Iterator;
class Solution {
    public String[] solution(int[][] line) {
        String[] answer = {};       
        HashMap<Long, HashSet<Long>> points = new HashMap<>();
        long minX = Long.MAX_VALUE;
        long maxX = Long.MIN_VALUE;
        
        //접점구하기
        for(int i=0; i<line.length-1; i++){
            long A = line[i][0];
            long B = line[i][1];
            long E = line[i][2];
            for(int j=i+1; j<line.length; j++){
                long C = line[j][0];
                long D = line[j][1];
                long F = line[j][2];
                
                double t= (double)(A*D)-(B*C);
                if(t==0) continue;
                double x = (double)(B*F-E*D)/t;
                double y = (double)(E*C-A*F)/t;
                
                // 점점중 x,y가 정수인 점들
                if(x%1==0 && y%1==0){
                    long longX = (long)x;
                    long longY = (long)y;
                    
                    minX = minX > longX? longX : minX;
                    maxX = maxX < longX? longX : maxX;
                    
                    HashSet<Long> set;
                    if(!points.containsKey(longY)) set = new HashSet<Long>();
                    else set = points.get(longY);
                    set.add(longX);
                    points.put(longY, set);
                }

            }
        }
            
        Object[] mapKey = points.keySet().toArray();
        Arrays.sort(mapKey);
        ArrayList<String> stars = new ArrayList<>();
        
        //별찍기
        int indexY = mapKey.length-1;
        for(long i=(long)mapKey[mapKey.length-1]; i>=(long)mapKey[0]; i--){
            StringBuilder star = new StringBuilder();
            for(long j=minX; j<=maxX; j++){
                star.append(".");
            }
            if(indexY<mapKey.length && i==(long)mapKey[indexY]){
                Iterator iter= points.get(mapKey[indexY]).iterator();
                while(iter.hasNext()){
                    star.setCharAt((int)Math.abs(minX-(long)iter.next()),'*');
                }
                indexY--;
            }
            stars.add(star.toString());
        }
         
        answer = new String[stars.size()];
        for(int i=0; i<stars.size(); i++){
            answer[i] = stars.get(i);
        }
        
        return answer;
    }
}
```