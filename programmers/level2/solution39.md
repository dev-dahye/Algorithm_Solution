# 프로그래머스 Level2 : 월간 코드 챌린지 시즌2 2개 이하로 다른 비트

- [문제](https://programmers.co.kr/learn/courses/30/lessons/77885)

```java
class Solution {
    long function(long x){
        StringBuilder binaryStr = new StringBuilder();
        binaryStr.append("00");
        binaryStr.append(Long.toBinaryString(x));
        
        for(int i=binaryStr.length()-1; i>0; i--){
            if(binaryStr.charAt(i)=='1' && binaryStr.charAt(i-1)=='0'){
                binaryStr.setCharAt(i,'0');
                binaryStr.setCharAt(i-1,'1');
                break;
            }
        }
        
        long result = Long.parseLong(binaryStr.toString(), 2);
        return result;
    }
    
    public long[] solution(long[] numbers) {
        long[] answer = new long[numbers.length];
        for(int i=0; i<numbers.length; i++){
            if(numbers[i]%2==0) answer[i] = numbers[i]+1;
            else answer[i] = function(numbers[i]);
        }
        
        return answer;
    }
}
```

## XOR연산 -> 테스트10,11 시간초과
```java
class Solution {
    long function(long x){
        long result = x+1;
        String binaryStr = "";
        int cnt = 0;
        long num = 0;
        while(true){
            num = x ^ result;
            binaryStr = Long.toBinaryString(num);
            for(int i=0; i<binaryStr.length(); i++){
                if(binaryStr.charAt(i)=='1') cnt++;
                if(cnt>2) break;
            }
            
            if(cnt<=2) break;
            result++;
            cnt = 0;
        }
        
        return result;
    }
    public long[] solution(long[] numbers) {
        long[] answer = new long[numbers.length];
        for(int i=0; i<numbers.length; i++){
            answer[i] = function(numbers[i]);
        }
        
        return answer;
    }
}
```