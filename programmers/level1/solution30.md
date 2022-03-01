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

## Comparator

```java
import java.util.Arrays;
import java.util.Comparator;

class Solution {
    public String[] solution(String[] strings, int n) {
        Arrays.sort(strings, new Comparator<String>(){
            @Override 
            public int compare(String s1, String s2){
                char c1 = s1.charAt(n);
                char c2 = s2.charAt(n);
                
                if(c1==c2){
                    return s1.compareTo(s2);
                } else{
                    return c1-c2;
                }
                
            }
        });
        
        return strings;
    }
}
```

## Lambda Expression

```java
import java.util.Arrays;

class Solution {
    public String[] solution(String[] strings, int n) {
         Arrays.sort(strings, (s1,s2)-> //s1, s2을 비교할 때     
                     s1.charAt(n) == s2.charAt(n)?  
                     s1.compareTo(s2) : s1.charAt(n)-s2.charAt(n));
                    // 같으면 문자열 비교 : 다르면 문자 비교
        
        return strings;
    }
}
```


<br>
<br>

- - -
## Refernce
- <https://st-lab.tistory.com/243>
- <https://velog.io/@hyeon930/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4-%EB%AC%B8%EC%9E%90%EC%97%B4-%EB%82%B4-%EB%A7%88%EC%9D%8C%EB%8C%80%EB%A1%9C-%EC%A0%95%EB%A0%AC%ED%95%98%EA%B8%B0-Java>
- <https://mangkyu.tistory.com/113>
- <https://github.com/jki503/Algorithm_Solution/blob/main/programmers/level1/solution32.md>