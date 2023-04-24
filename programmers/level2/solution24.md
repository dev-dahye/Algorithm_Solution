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
## 람다 사용 (java8 이상)
```java
import java.util.*;
class Solution {
    public String solution(int[] numbers) {
        String[] strarr = new String[numbers.length];
        
        for(int i=0; i<numbers.length; i++){
            strarr[i] = Integer.toString(numbers[i]);
        }
        // sort의 두번째 argument는 Comparator로 정해져 있음 -> 생략가능
        // Comparator에는 compare 메소드 밖에 없음 -> 생략가능
        // strarr에 String타입이기때문에 타입 생략 가능 
        // 구현내용이 한줄 이기때문에 return 생략 가능
        Arrays.sort(strarr,(s1, s2)->(s2+s1).compareTo(s1+s2)); 
        String answer = "";

        if(strarr[0]=="0") return "0"; 
        for(String s : strarr){
            answer += s;
        }
        return answer;
    }
}
```

## Stream 사용 (java8 이상)
```java
import java.util.*;
import java.util.stream.*;
class Solution {
    public String solution(int[] numbers) {
        String answer = IntStream.of(numbers)
        //.mapToObj(n -> String.valueOf(n)) 밑에 처럼 생략가능
        .mapToObj(String::valueOf)
        .sorted((s1,s2)->(s2+s1).compareTo(s1+s2))
        .collect(Collectors.joining());

        if(answer.startsWith("0")) return "0"; 
            return answer;
    }
}
```