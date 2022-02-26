# 프로그래머스 Level1 : 2021 KAKAO BLIND RECRUITMENT 신규 아이디 추천



- [문제](https://programmers.co.kr/learn/courses/30/lessons/72410)

```java
import java.util.regex.Pattern;
class Solution {
    public String solution(String new_id) {
        String answer = "";
        
        //1단계
        new_id = new_id.toLowerCase();
        //2단계 
        String pattern = "[^\\w\\.\\-]";
        new_id=new_id.replaceAll(pattern,"");        
        //3단계 
        while(new_id.indexOf("..")!=-1)
            new_id=new_id.replaceAll("\\.\\.","\\.");        
        //4단계
        new_id = new_id.replaceAll("^\\.","");
        new_id = new_id.replaceAll("\\.$","");    
        //5단계 
        if(new_id.equals(""))
            new_id = "a";
        //6단계 
        if(new_id.length()>=16)
            new_id=new_id.substring(0,15);
        new_id = new_id.replaceAll("\\.$","");
        //7단계       
        while(new_id.length()<=2)
            new_id+=new_id.charAt(new_id.length()-1);
            
        answer = new_id;
        return answer;
    }
}
```

## 정규표현식
|표현| 설명|
|---|---|
|`^`   |문자열 시작|
|`$`   |문자열 종료|
|`.`   |임의의 한 문자(단 \은 넣을 수 없음)|
|`*`   |앞 문자가 없을 수도 무한정 많을 수도 있음|
|`+`   |앞 문자가 하나 이상|
|`?`   |앞 문자가 없거나 하나 있음|
|`[ ]` |문자의 집합이나 범위를 나타내며 두 문자 사이는 - 기호로 범위를 나타냅니다. [] 내에서 ^ 가 선행하여 존재하면 not을 나타낸다.|
|`{ }` |횟수 또는 범위를 나타냅니다.|
|`( )` |소괄호 안의 문자를 하나의 문자로 인식|
|`|`   |패턴 안에서 or 연산을 수행할 때 사용|
|`\`	|정규 표현식 역슬래시(\)는 확장문자 (역슬래시 다음에 일반 문자가 오면 특수문자로 취급하고 역슬래시 다음에 특수문자가 오면 그 문자 자체를 의미)|
|`\b`	|단어의 경계|
|`\B`	|단어가 아닌것에 대한 경계|
|`\A`	|입력의 시작 부분|
|`\G`	|이전 매치의 끝|
|`\Z`	|입력의 끝이지만 종결자가 있는 경우|
|`\z`	|입력의 끝|
|`\s`	|공백 문자|
|`\S`	|공백 문자가 아닌 나머지 문자|
|`\w`	|알파벳이나 숫자|
|`\W`	|알파벳이나 숫자를 제외한 문자|
|`\d`	|숫자 [0-9]와 동일|
|`\D`	|숫자를 제외한 모든 문자|
|`(?i)`	|앞 부분에 (?!)라는 옵션을 넣어주게 되면 대소문자는 구분하지 않습니다.|


<br>
<br>

- - -
## Refernce
- <https://hardlearner.tistory.com/288>
- <https://codechacha.com/ko/java-regex/>