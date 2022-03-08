# 프로그래머스 Level2 : 탐욕법(Greedy) 조이스틱

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42860)

```java
class Solution {
 class Solution {
    public int solution(String name) {
        int answer = 0;
        final char halfAlpa = 'A' + ('Z'-'A') / 2;
        int l = name.length();
        
        //최대로 가질 수 있는 min값은 끝까지 가는것
        int min_move = l-1;
        
        for(int i=0; i<l; i++) {
        	char c = name.charAt(i);
            if(c<=halfAlpa) answer += (int)c-'A';
            else answer += (int)'Z'-c + 1;   
        	
        	//'A'를 만났을경우 'A'가 몇개 붙어있는지 조사하고 뒤돌아 가는 경우에 몇 번의 move가 발생하는지
        	int next = i+1;// 현재 다음 위치부터
        	//다음이 A라면 next++
        	while(next<l && name.charAt(next) == 'A'){
        		next++;
            }

            // 오른쪽으로 처음 움직였을때 
            // 첫위치로 돌아간 후 (i만큼 움직였고+i만큼 되돌아감)
            // 'A'가 아닐때까지 왼쪽으로 움직이기
        	min_move = Math.min(min_move, (l-next) + i*2);
            
            //왼쪽으로 처음 움직였을경우
            // 첫위치로 돌아간 후 'A'가 아닐때까지 오른쪽으로 움직이기
            min_move = Math.min(min_move, (l-next)*2 + i);
        }
        
        answer += min_move;
        return answer;
    }
}
```

<br>
<br>

- - -

## Reference
-<https://github.com/jki503/Algorithm_Solution/blob/main/programmers/level2/solution57.md>
-<https://parksuu.github.io/139-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4-%EC%A1%B0%EC%9D%B4%EC%8A%A4%ED%8B%B1-(java)/>