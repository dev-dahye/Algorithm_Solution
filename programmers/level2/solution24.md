# 프로그래머스 Level2 : 정렬 가장 큰 수

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42746#)

```java
import java.util.Collections;
import java.util.Comparator;
import java.util.ArrayList;

class Solution {
    public String solution(int[] numbers) {
        String answer = "";
        ArrayList<String> numList = new ArrayList<>();
        //String[] numArray = new String[numbers.length];
        for(int i=0; i<numbers.length; i++){
            numList.add(Integer.toString(numbers[i]));
        }
        
        Collections.sort(numList, new Comparator<String>(){
            @Override
            public int compare(String s1, String s2){
                return (s2+s1).compareTo(s1+s2);    
            }
        });
        
        StringBuilder sb= new StringBuilder();
        for(String n : numList){
            sb.append(n);
        }
        
        answer = sb.toString().charAt(0) == '0' ? "0" : sb.toString();
        
        return answer;
    }
}
```