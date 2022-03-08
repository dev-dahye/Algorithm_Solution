# 프로그래머스 Level2 : 2021 KAKAO BLIND RECRUITMENT 순위 검색

- [문제](https://programmers.co.kr/learn/courses/30/lessons/72412)

## 이진탐색
```java
import java.util.HashMap;
import java.util.Map;
import java.util.ArrayList;
import java.util.Collections;

class Solution {
    HashMap<String, ArrayList<Integer>> allInfo = new HashMap<>();
    
    void dfs(String key, int index, String[] info){
        StringBuilder sb = new StringBuilder();
        if(index==4){
            if(!allInfo.containsKey(key)){
                allInfo.put(key,new ArrayList<Integer>());
            }
            allInfo.get(key).add(Integer.parseInt(info[4]));
            return;
        }
        
        dfs(key+"-", index+1, info);
        dfs(key+info[index], index+1, info);
    }
    
    int search(String q, int score) {
        if(!allInfo.containsKey(q)) return 0;
        
        ArrayList<Integer> scoreList = allInfo.get(q); 
        int start= 0, end = scoreList.size()-1;
        while(start<=end) {
            int mid =(start+end)/2;
            if(scoreList.get(mid) <score) {
                start = mid+1;	
            }else {
                end = mid-1;
            }
        }

        // score보다 높은 점수의 갯수 
        return scoreList.size()-start;
    }
    
    
    public int[] solution(String[] info, String[] query) {
        int[] answer = new int[query.length];
        
        // 1. info 모든 경우의 수 map에 저장 
        for(String inf :info){
            dfs("",0,inf.split(" "));
        }
        
        
        // 2. map에 저장된 점수 list 오름차순으로 정렬 	
        for(Map.Entry<String,ArrayList<Integer>> entry : allInfo.entrySet()) {
        	Collections.sort(entry.getValue());
        }
        
        // 3. 이진 탐색
        for(int i=0; i<query.length; i++) {
        	query[i] = query[i].replace(" and ", "");
        	String[] q = query[i].split(" ");
        	int score = Integer.parseInt(q[1]);

        	answer[i] = search(q[0], score);
        }
        return answer;
    }
}
```

## 배열 -> 효율성X
```java
class Solution {
    public int[] solution(String[] info, String[] query) {
        int[] answer = new int[query.length];
        
        String[][] apct = new String[info.length][5];
        String[][] qry = new String[query.length][5];
        
        int index = 0;
        for(String str : info){
            String[] arr = str.split(" ");
            apct[index][0] = arr[0];
            apct[index][1] = arr[1];
            apct[index][2] = arr[2];
            apct[index][3] = arr[3];
            apct[index][4] = arr[4];
            index++;
        }
        
        index=0;
        for(String str : query){
            String[] arr = str.split(" and ");
            qry[index][0] = arr[0];
            qry[index][1] = arr[1];
            qry[index][2] = arr[2];
            qry[index][3] = arr[3].split(" ")[0];
            qry[index][4] = arr[3].split(" ")[1];
            index++;
        }
        int cnt = 0;
        for(int j=0; j<qry.length; j++){
           for(String[] a : apct){
                for(int i=0; i<5; i++){
                    if(i<4 && !qry[j][i].equals("-") && !qry[j][i].equals(a[i])){
                        break;
                    }
                    int score1 = Integer.parseInt(qry[j][4]);
                    int score2 = Integer.parseInt(a[4]);
                    if(i==4 && !qry[j][4].equals("-")&& score1<=score2){
                        cnt++;
                    }
                }
            }
            answer[j] = cnt;
            cnt = 0;
        }
        
        return answer;
    }
}
```


<br>
<br>

- - -

## Reference
-<https://loosie.tistory.com/265>
-<https://ko.wikipedia.org/wiki/%EC%9D%B4%EC%A7%84_%EA%B2%80%EC%83%89_%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98>