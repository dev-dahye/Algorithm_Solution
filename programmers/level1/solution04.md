# 프로그래머스 Level1 : 2021 카카오 채용연계형 인턴십 숫자 문자열과 영단어



- [문제](https://programmers.co.kr/learn/courses/30/lessons/81301)

```java
class Solution {
    public int solution(String s) {
        int answer = 0;
        char currC,nextC;
        
        for(int i=0; i<s.length(); i++){
            currC = s.charAt(i);
            if(currC<'0' || currC>'9'){
                switch(currC){
                    case 'z':
                        s= s.replace("zero","0");
                        break;
                    case 'o':
                        s= s.replace("one","1");
                        break;
                    case 't':
                        nextC = s.charAt(i+1);
                        if(nextC=='w')
                            s = s.replace("two","2");        
                        else
                            s= s.replace("three","3");
                        break;
                    case 'f':
                        nextC = s.charAt(i+1);
                        if(nextC=='o')
                            s = s.replace("four","4");        
                        else
                            s = s.replace("five","5");
                        break;     
                    case 's':
                        nextC = s.charAt(i+1);
                        if(nextC=='i')
                            s = s.replace("six","6");        
                        else
                            s = s.replace("seven","7");
                        break;
                    case 'e':
                        s = s.replace("eight","8");
                        break;                 
                    case 'n':
                        s = s.replace("nine","9");
                        break;
                }
            }
        }
        
        answer = Integer.parseInt(s);
        return answer;
    }
}
```