# 프로그래머스 Level2 : 2019 KAKAO BLIND RECRUITMENT 후보키

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42890#)

```java
import java.util.HashSet;
import java.util.ArrayList;
import java.util.Iterator;
class Solution {
    boolean[] isVisited;
    HashSet<String> keySet = new HashSet<>();
    void dfs(String cKey, int index, String[][] relation){
        if(!cKey.equals("")){
            HashSet<String> tupleSet = new HashSet<>();    
            for(int i=0; i<relation.length; i++){
                StringBuilder sb = new StringBuilder();
                for(char c : cKey.toCharArray()){
                    sb.append(relation[i][c-'0']);
                }
                
                if(!tupleSet.add(sb.toString())){
                    for(int j=index; j<isVisited.length; j++){
                        if(!isVisited[j]){
                            isVisited[j] = true;
                            dfs(cKey+j,j,relation);
                            isVisited[j] = false;
                        }
                    }
                    return;
                }
            }
            keySet.add(cKey);
        }
        for(int i=index; i<isVisited.length; i++){
            if(!isVisited[i]){
                isVisited[i] = true;
                dfs(cKey+i,i,relation);
                isVisited[i] = false;
            }
        }
        
    }
    public int solution(String[][] relation) {
        int answer = 0;
        isVisited = new boolean[relation[0].length];
        
        // 유일성
        dfs("",0,relation);
        
        ArrayList<String> keyList = new ArrayList<>();
        
        Iterator<String> iter = keySet.iterator();
        while(iter.hasNext()){
            keyList.add(iter.next());
        }


        // 최소성
        for(int i=0; i<keyList.size(); i++){
            String cKey = keyList.get(i);
            for(int j=0; j<keyList.size(); j++){
                String key = keyList.get(j);
                if(key.equals("X") || key.equals(cKey)) continue;
                for(char c : cKey.toCharArray()){
                    keyList.set(j,key);
                    if(key.indexOf(c)==-1){
                        break;
                    }
                    keyList.set(j,"X");
                }
                
            }
        }
        for(String key : keyList){
            if(!key.equals("X")) answer++;
        }
        
        return answer;
    }
}
```