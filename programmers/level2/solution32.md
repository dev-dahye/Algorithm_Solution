# 프로그래머스 Level2 : 의상 (리뉴얼 전 : 해시 위장)

- [문제](https://school.programmers.co.kr/learn/courses/30/lessons/42578)

```java
import java.util.*;
class Solution {
    public int solution(String[][] clothes) {
        HashMap<String,Integer> itemMap = new HashMap<>();
        for(String[] c : clothes){
            itemMap.put(c[1],(itemMap.getOrDefault(c[1],0)+1));
        }
        
        //해당 의상종류를 안입을 경우까지 포함해서 계산
        //headgear: yellowhat, green_turban, none (3가지)
        //eyewear: bluesunglasses, none (2가지)
        int answer = 1;
        /*
        for(String key : itemMap.keySet()){ 
            answer *= itemMap.get(key)+1;
        }
        */
       for(Integer c : itemMap.values()){ 
            answer *= c+1;
        }
        // 아무것도 안입은 경우 : -1 
        return answer-1;
    }
}
```

## Stream 이용하기
```java
import java.util.*;
class Solution {
    public int solution(String[][] clothes) {
        HashMap<String,Integer> itemMap = new HashMap<>();
        int answer = Arrays.stream(clothes) // clothes[i]의 값을 c로 매핑 
                .map(c->c[1])               // c[1]의 값만 꺼내서
                .distinct()                 // 중복없이
                // type으로 매핑->type이랑 같은 c[1]을 필터링해서 count(return type:long) 
                // int로 타입 변환
                .map(type->(int)Arrays.stream(clothes).filter(c->c[1].equals(type)).count())
                .map(c -> c+1)      // 나온 값에 +1 해서
                .reduce(1,(total,n)->total*n);  // 누적해서 곱한값
                //Stream.reduce() : Stream의 요소들을 하나의 데이터로 만드는 작업을 수행

        return answer-1;
    }
}
```

#### 테스트 1 시간초과
```java
import java.util.*;
class Solution {
    HashMap<String,Integer> itemMap = new HashMap<>();
    String[] itemArr;
    int combination(String[] select, int n, int r, int index, int con){
        int result = 0;
        if(con == r){
            int num = 1;
            for(int i=0; i<r; i++){
                num *= itemMap.get(select[i]);
            }
            result += num;
            return result;
        } else if(con>=r || index >= itemArr.length){
            return result;
        }else{
            result += combination(select,n,r,index+1,con);
            select[con] = itemArr[index];
            result += combination(select,n,r,index+1,con+1);
        }
        return result;
    }
    public int solution(String[][] clothes) {
        for(String[] c : clothes){
            itemMap.put(c[1],(itemMap.getOrDefault(c[1],0)+1));
        }
        itemArr = new String[itemMap.size()];
        int index = 0;
        for(String key : itemMap.keySet()){
            itemArr[index++] = key;
        }

        int answer = 0;
        // 옷을 r개 착용하는 경우
        for(int r=1; r<=itemMap.size(); r++){
            int result = combination(new String[r],itemMap.size(),r,0,0);    
            answer += result;
        }
        
        return answer;
    }
}
```
<br>
<br>

- - -
## Reference
stream reduce 참고 : <https://codechacha.com/ko/java8-stream-reduction/>