# 프로그래머스 Level2 : 월간 코드 챌린지 시즌3 n^2 배열 자르기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/87390)

```java
class Solution {
    public int[] solution(int n, long left, long right) {
        int[] answer = new int[(int)(right-left)+1];
        int index = 0;
        for(long i = left; i<=right; i++){
            answer[index++] = Math.max((int)(i/n),(int)(i%n)) + 1;
        }
        return answer;
    }
}
```

```java
class Solution {
    public int[] solution(int n, long left, long right) {
        int[] answer = new int[(int)(right-left)+1];
        
        int sRow = (int)(left/n);   
        int sCol = (int)(left%n);   
        int eRow = (int)(right/n);  
        int eCol = (int)(right%n);  
        
        int index = 0;
        for(int i=sCol; i<n; i++){
            if(index>(int)(right-left)) break;
            if(i<sRow){
                answer[index++] = sRow+1;
            } else {
                answer[index++] = i+1;
            }
        }
        
        for(int i=sRow+1; i<eRow; i++){
            if(index>(int)(right-left)) break;
            for(int j=0; j<i; j++){
                answer[index++] = i+1;
            }
            for(int j=i; j<n; j++){
                answer[index++] = j+1;
            }
        }

        for(int i=0; i<=eCol; i++){
            if(index>(int)(right-left)) break;
            if(i<eRow){
                answer[index++] = eRow+1;
            } else {
                answer[index++] = i+1;
            }
        }
        /*
        for(int i : answer){
            System.out.print(i+" ");
        }
        */
        return answer;
    }
}
```

<br>
<br>

- - -

## Reference
- <https://hyunjiishailey.tistory.com/439>