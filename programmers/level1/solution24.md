# 프로그래머스 Level1 : 2018 KAKAO BLIND RECRUITMENT [1차] 비밀지도

- [문제](https://programmers.co.kr/learn/courses/30/lessons/17681)

```java
import java.util.Stack;
class Solution {
    public String[] solution(int n, int[] arr1, int[] arr2) {
        String[] answer = new String[n];
        Stack<Integer> map1 = new Stack<>();   
        Stack<Integer> map2 = new Stack<>();
        int m1;
        int m2;
        
        int m1Size;
        int m2Size;
        
        StringBuilder sb = new StringBuilder();
        
        for(int i=0; i<n; i++){
            while(arr1[i]!=0){
                map1.push(arr1[i]%2);    
                arr1[i]/=2;    
            }         
            m1Size = map1.size();
            
            while(arr2[i]!=0){
                map2.push(arr2[i]%2);    
                arr2[i]/=2;    
            }
            m2Size = map2.size();
            
            for(int j=0; j<n; j++){
                if(m1Size<n){
                     m1 = 0;
                    m1Size++;
                } else{
                    m1 = map1.pop();    
                }
                
                if(m2Size<n){
                    m2 = 0;
                    m2Size++;
                } else{
                    m2 = map2.pop();    
                }
                
                if(m1==1 || m2==1){
                    sb.append("#");
                } else { //m1==0&&m2==0
                    sb.append(" ");
                }
            }
            
            answer[i] = sb.toString();
            sb.delete(0, n+1);
        }
        return answer;
    }
}
```

## String.format

```java
class Solution {
    public String[] solution(int n, int[] arr1, int[] arr2) {
        String[] answer = new String[n];
        
        for(int i=0; i<n; i++){
            answer[i] = String.format("%0"+n+"d", 
                    Long.parseLong(Integer.toBinaryString(arr1[i] | arr2[i])));
        }
        
        for(int i=0; i<n; i++){
            answer[i] = answer[i].replace("1","#").replace("0"," ");
        }
        
        return answer;
    }
}
```

<br>
<br>

- - -
## Reference
- <https://blog.jiniworld.me/68>
- <https://dpdpwl.tistory.com/92>
- <https://github.com/jki503/Algorithm_Solution/blob/main/programmers/level1/solution26.md>

