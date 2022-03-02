# 프로그래머스 Level1 : 연습문제 제일 작은 수 제거하기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12935)

```java
class Solution {
    public int[] solution(int[] arr) {
        int l = arr.length;
        if(l==1) return new int[]{-1};
        
        int[] answer = new int[l-1];
        int min = 0;
        
        for(int i=1; i<l; i++){
            if(arr[min]>arr[i])
                min =i;
        }
    
        int index =0;
        for(int i=0; i<l; i++){
            if(i==min) continue;
            answer[index++] = arr[i];
        }
        return answer;
    }
}
```