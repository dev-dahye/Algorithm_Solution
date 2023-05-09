# 프로그래머스 Level3 : 예산

- [문제](https://school.programmers.co.kr/tryouts/78111/challenges)

# 이분 탐색 binary search

* 이분탐색의 조건 : 데이터가 정렬이 되어있어야 한다. 
* 범위를 줄여가면서 값을 찾는 방법    
* max~min의 중간값mid 을 상한선으로 정해서 예산을 계산   
* 예산을 넘지않았다면 : mid~max 사이로 범위를 새로 조정    
* 예산을 넘었다면 : min~mid 사이로 범위를 새로 조정    
* 최소값과 최대값이 같아질때 까지 반복 

```java
class Solution {
    public int solution(int[] budgets, int M) {
        int min = 0;
        int max = 0;
        for(int b: budgets){
            if(b>max) max = b;
        }
        int answer = 0;

        while(min <= max){
            int mid = (min+max)/2;

            int sum = 0;
            for(int b:budgets){
                if(b > mid){
                    sum += mid;
                } else {
                    sum += b;
                }
            }
            if(sum<=M){
                min = mid + 1;
                answer = mid;
            } else {
                max = mid - 1 ;
            }
        }
        return answer;
    }
}
```
## Stream으로 리팩토링
```java
import java.util.stream.*;
class Solution {
    public int solution(int[] budgets, int M) {
        int min = 0;
        int max = IntStream.of(budgets).max().orElse(0);
        //IntStream.of(budgets).max() => 리턴타입 : Optional(Int) : 값이 없을 수도 있음
        //.orElse(0) => 값이 없을 경우 0 
        
        int answer = 0;

        while(min <= max){
            final int mid = (min+max)/2; // Stream안에서 가변변수를 사용X-> final int
            int sum = IntStream.of(budgets)
            .map(b -> Math.min(b,mid))
            .sum();

            if(sum<=M){
                min = mid + 1;
                answer = mid;
            } else {
                max = mid - 1 ;
            }
        }
        return answer;
    }
}
```


#### 보완 필요 ...

```java
import java.util.*;
class Solution {
    int calBudget(int[] budgets, int limit){
        int total = 0;
        for(int b : budgets){
            total += (b>limit)? limit : b;
        }
        return total;
    }
    int findLimit(int[] budgets, int M, int min, int max){
        int mid = (max+min)/2;
        int calB = calBudget(budgets,mid);
        if(min>max){
            return max;
        }
        if(calB>=M){
            max = findLimit(budgets,M,min,mid-1);
        } else{
            max = findLimit(budgets,M,mid+1,max);
        }
        return max;
    }
    
    public int solution(int[] budgets, int M) {
        Arrays.sort(budgets);
        int maxB = budgets[budgets.length-1];
        int minB = budgets[0];
        
        // 예산요청이 전부 가능한 경우 
        if(calBudget(budgets,maxB)<=M) return maxB;

        // 상한선이 필요한 경우 
        int answer = findLimit(budgets, M, minB, maxB);
        return answer;
    }
}
```