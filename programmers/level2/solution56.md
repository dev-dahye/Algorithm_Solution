# 프로그래머스 Level2 : 2018 KAKAO BLIND RECRUITMENT [3차] 파일명 정렬

- [문제](https://programmers.co.kr/learn/courses/30/lessons/17686)

```java
import java.util.Arrays;

class Solution {
    class File implements Comparable<File>{
        String name;
        int index;
        String head;
        int number;
        String tail;
        
        public File(String file, int index){
            this.name = file;
            this.index = index;
            int index1 = 0;
            int index2 = 0;
            for(int i=1; i<file.length(); i++){
                char c = file.charAt(i);
                if(index1==0 && Character.isDigit(c)){
                    index1 = i;
                }
                if(index1!=0 && index2==0 && !Character.isDigit(c)){
                    index2 = i;
                    break;
                }
            }
            if(index2==0) index2 = file.length();
            if(index2>=index1+5) index2 = index1+5;
            
            this.head = file.substring(0,index1).toLowerCase();
            
            this.number = Integer.parseInt(file.substring(index1,index2));
            this.tail = file.substring(index2);
        }
        
        @Override
        public int compareTo(File f){
            if(this.head.equals(f.head)){
                if(this.number==f.number){
                    return this.index-f.index;
                }else{
                    return this.number-f.number;   
                }
            }else{
                return this.head.compareTo(f.head);
            }
        }
    }
    public String[] solution(String[] files) {
        int len = files.length;
        String[] answer = new String[len];
        File[] fileArr = new File[len];
        for(int i=0; i<len; i++){
            fileArr[i] = new File(files[i],i);
        }
        
        Arrays.sort(fileArr);
        for(int i=0; i<len; i++){
            answer[i] = fileArr[i].name;
        }
        return answer;
    }
}
```
