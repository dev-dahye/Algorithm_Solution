# 프로그래머스 Level1 : 연습문제 문자열 내 마음대로 정렬하기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12915)

```java
import java.util.ArrayList;
import java.util.Collections;

class Solution {
    public String[] solution(String[] strings, int n) {        
        String[] answer = new String[strings.length];
        
        ArrayList<Character> nthList = new ArrayList<>();
        ArrayList<Character> sortList = new ArrayList<>();
        ArrayList<String> dictionary = new ArrayList<>();
        
        ArrayList<String> answerArrayList = new ArrayList<>();
        
        for(String s : strings){
            nthList.add(s.charAt(n));
        }
        
        sortList = new ArrayList<>(nthList);
        Collections.sort(sortList); 
        
        for(int j=0; j<sortList.size(); j++){
            for(int i=0; i<nthList.size(); i++){
                if(sortList.get(j) == nthList.get(i)){
                    dictionary.add(strings[i]);
                    nthList.set(i,' ');
                }
            }

            Collections.sort(dictionary); 
            for(int d=0; d<dictionary.size(); d++){
                answerArrayList.add(dictionary.get(d));
            }
            dictionary.clear();
        }       
        
        int i = 0;
        for(String str : answerArrayList){
            answer[i++] = str;
        }
        
        return answer;
    }
}
```