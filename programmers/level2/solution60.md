# 프로그래머스 Level2 : 2022 KAKAO BLIND RECRUITMENT k진수에서 소수 개수 구하기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/92335)

```java
class Solution {
    boolean isPrime(long num){
        if(num<=1) return false;
        for(int i=2; i<=Math.sqrt(num); i++){
            if(num%i==0) return false;
        }
        
        return true;
    }
    
    String toKBaseNumber(int num, int k){
        StringBuilder sb = new StringBuilder();
        while(num!=0){
            sb.insert(0,num%k);
            num/=k;
        }
        
        return sb.toString();
    }
    
    public int solution(int n, int k) {
        int answer = 0;
        String number = toKBaseNumber(n,k);
        
        StringBuilder sb = new StringBuilder();
        boolean zeroCheck = false;
        for(int i=0; i<number.length(); i++){
            char c = number.charAt(i);
            if(c!='0'){
                sb.append(c);
                if(i==number.length()-1|| number.charAt(i+1)=='0'){
                    if(!sb.toString().equals("") && isPrime(Long.parseLong(sb.toString()))){
                        answer++;
                    }
                    sb.delete(0,sb.length());
                }
            } 
        }
         
        return answer;
    }
}
```