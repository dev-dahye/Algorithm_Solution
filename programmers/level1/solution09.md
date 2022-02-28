# 프로그래머스 Level1 :Summer/Winter Coding(~2018) 소수 만들기
 

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12977)

```java
class Solution {
    public int solution(int[] nums) {
        int answer = 0;
        int l = nums.length;
        int sum = 0;
        boolean isPrime = true;
        
        for(int x=0; x<l-2; x++){
            for(int y=x+1; y<l-1; y++){
                for(int z=y+1; z<l; z++){
                    sum = nums[x]+nums[y]+nums[z];
                    for(int i=2; i<=Math.sqrt(sum); i++){
                        if(sum % i == 0){
                            isPrime = false;
                            break;
                        } 
                    }
                    if(isPrime){
                        answer ++;
                    } else{
                        isPrime = true;
                    }
                }
            }
        }

        return answer;
    }
}
```