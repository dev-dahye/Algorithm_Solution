# 프로그래머스 Level2 : 탐욕법(Greedy) 큰 수 만들기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42883#)

```java
class Solution {
    public String solution(String number, int k) {
        int len = number.length()-k;
        
        int max = 0;
        for(int i=0; i<k; i++){
            if(number.charAt(max)<number.charAt(i)){
                max = i;   
            }
        } 
        
        StringBuilder sb = new StringBuilder(number.substring(max));
        int l = sb.length();
        int index =0;
        while(l!=len){
            for(int i=0; i<l-1; i++){
                char c1 = sb.charAt(i);
                char c2 = sb.charAt(i+1);
                if(c1<c2){
                    index = i;
                    break;
                } else{
                    index= i+1;
                }
            }
            sb.deleteCharAt(index);
            l = sb.length();
        }
                
        return sb.toString();
    }
}
```