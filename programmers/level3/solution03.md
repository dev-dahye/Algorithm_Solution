# 프로그래머스 Level3 : 2021 Dev-Matching: 웹 백엔드 개발자(상반기) 다단계 칫솔 판매

- [문제](https://programmers.co.kr/learn/courses/30/lessons/77486?language=java)

```java
import java.util.HashMap;
class Solution {
    HashMap<String,Integer> memberIndex = new HashMap<>();
    int[] answer;
    void calculate(String name, int pay, String[] referral){
        int m = memberIndex.get(name);
        answer[m]+=pay-(int)(pay * 0.1);
        if(referral[m].equals("-") || pay<1)
            return;
        else {
            calculate(referral[m], (int)(pay*0.1), referral);
        }

    }
    public int[] solution(String[] enroll, String[] referral, String[] seller, int[] amount) {
        int index = 0;
        for(int i=0; i<enroll.length; i++){
            memberIndex.put(enroll[i],index++);
        }
        answer = new int[memberIndex.size()];

        for(int i=0; i<seller.length; i++){
            int pay = amount[i]*100;
            calculate(seller[i], pay, referral);
        }
        return answer;
    }
}
```