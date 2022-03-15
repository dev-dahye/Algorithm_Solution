# 프로그래머스 Level2 : Summer/Winter Coding(~2018) 스킬트리

- [문제](https://programmers.co.kr/learn/courses/30/lessons/49993)

```java
class Solution {
    public int solution(String skill, String[] skill_trees) {
        int answer = 0;
        
        if(skill.equals("")) return skill_trees.length;
        
        for(String st : skill_trees){
            int[] order = new int[skill.length()];
            
            for(int i=0; i<skill.length(); i++){
                char c = skill.charAt(i);
                int index = st.indexOf(c);
                if(index==-1) order[i] = 27;
                else order[i] = index;
            }
            
            int o = order[0];
            boolean isOrder = true;
            for(int i=1; i<skill.length(); i++){
                if(o>order[i]){
                    isOrder = false;
                    break;
                }
                o = order[i];
            }
            
            if(isOrder){
                answer++;
            }
        }
        return answer;
    }
}
```