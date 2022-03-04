# 프로그래머스 Level2 : 2017 카카오코드 본선 단체사진 찍기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/1835)

```java
class Solution {
    String[] friends={"A","C","F","J","M","N","R","T"};
    int cnt = 0;
    
    //순열 만들기
    void dfs(String names, boolean[] isVisited, String[] datas){    
        if(names.length()==7){
            if(isCorrect(names,datas)){
                cnt++;
            }
            return;
        }
        
        for(int i=0; i<8; i++){
            if(!isVisited[i]){
                isVisited[i] = true;
                dfs(names+friends[i],isVisited,datas);
                isVisited[i] = false;
            }
        }
        
    }
    
    //제대로 줄섰는지 확인
    boolean isCorrect(String name, String[] datas){
        for(String d : datas){
            int position1 = name.indexOf(d.charAt(0));
            int position2 = name.indexOf(d.charAt(2));
            char sign = d.charAt(3);
            int distance = d.charAt(4)-'0';
            
            if(sign=='='){
                if(Math.abs(position1-position2)!=distance+1) return false;
            } else if(sign=='<'){
                if(!(Math.abs(position1-position2)<distance+1))
                    return false;
            } else{
               if(!(Math.abs(position1-position2)>distance+1))
                    return false;
            }  
        }
        return true;
    }
    
    public int solution(int n, String[] data) {
        int answer = 0;
        // 해당 프렌즈를 줄세웠는지
        boolean[] isVisited = new boolean[8];
        dfs("", isVisited, data);
        
        answer = cnt;
        return answer;
    }
}
```