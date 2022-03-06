# 프로그래머스 Level2 : 스택/큐 프린터

- [문제](https://programmers.co.kr/learn/courses/30/lessons/42587)

## for문
```java
import java.util.Queue;
import java.util.LinkedList;
class Solution {
    class Document{
        int priority;
        boolean isMine;
        
        Document(int priority, boolean isMine){
            this.priority = priority;
            this.isMine=isMine;
        }
    }
    
    public int solution(int[] priorities, int location) {
        int answer = 0;
        int l = priorities.length;
        Queue<Document> print = new LinkedList<>();
       
        for(int i=0; i<l; i++){
            if(i==location) print.offer(new Document(priorities[i],true));
            else print.offer(new Document(priorities[i],false));
        }
        
        while(!print.isEmpty()){
            int s = print.size();
            Document doc = print.poll();
            for(Document d:print){
                if(doc.priority<d.priority){
                    print.offer(doc);
                    break;
                }
            }
            
            if(print.size()==s-1){
                answer++;    
                if(doc.isMine) return answer;
            }
        }
        
        return answer;
    }
}
```


## Stream 이용
```java
import java.util.Queue;
import java.util.LinkedList;
import java.util.stream.Collectors;
import java.util.stream.IntStream;

class Solution {
    class Document{
        int priority;
        boolean isMine;
        
        Document(int priority, boolean isMine){
            this.priority = priority;
            this.isMine=isMine;
        }
        
    }
    
    public int solution(int[] priorities, int location) {
        int answer = 0;
        int l = priorities.length;
        
        Queue<Document> print = IntStream.range(0, priorities.length)
                .mapToObj(i -> new Document(priorities[i], i == location))
                .collect(Collectors.toCollection(LinkedList::new));

        
        while(!print.isEmpty()){
            Document doc = print.poll();
            
            if (print.stream().anyMatch(d -> d.priority > doc.priority)) {
                print.offer(doc);
            
            } else {
                answer++;
                if (doc.isMine){
                    break;
                }
            }
        }
        
        return answer;
    }
}
```


## for문와 Stream 수행시간
|테스트|for문|Stream|
|---|---|---|
|테스트 1 〉	|통과 (0.92ms, 77.5MB)|   통과 (4.19ms, 72.6MB)|
|테스트 2 〉    |통과 (2.10ms, 76.8MB)|   통과 (6.32ms, 74.9MB)|
|테스트 3 〉	|통과 (0.53ms, 76.3MB)|   통과 (3.49ms, 69.2MB)|
|테스트 4 〉	|통과 (0.50ms, 76.8MB)|   통과 (3.63ms, 76.1MB)|
|테스트 5 〉	|통과 (0.42ms, 73.4MB)|   통과 (3.05ms, 74.6MB)|
|테스트 6 〉	|통과 (0.73ms, 76.5MB)|   통과 (4.24ms, 78.2MB)|
|테스트 7 〉	|통과 (0.78ms, 73.2MB)|   통과 (3.78ms, 76.9MB)|
|테스트 8 〉	|통과 (1.85ms, 74.3MB)|   통과 (5.57ms, 74.3MB)|
|테스트 9 〉	|통과 (1.39ms, 75.2MB)|   통과 (3.38ms, 77.1MB)|
|테스트 10 〉	|통과 (0.70ms, 82.7MB)|   통과 (4.33ms, 79.7MB)|
|테스트 11 〉	|통과 (1.91ms, 76.4MB)|   통과 (5.20ms, 75.1MB)|
|테스트 12 〉	|통과 (0.46ms, 77.8MB)|   통과 (3.23ms, 75.4MB)|
|테스트 13 〉	|통과 (1.30ms, 76.2MB)|   통과 (5.09ms, 75.8MB)|
|테스트 14 〉	|통과 (0.34ms, 74.6MB)|   통과 (3.04ms, 76MB)  |
|테스트 15 〉	|통과 (0.37ms, 78.3MB)|   통과 (3.33ms, 73.3MB)|
|테스트 16 〉	|통과 (0.52ms, 73.1MB)|   통과 (3.33ms, 76.1MB)|
|테스트 17 〉	|통과 (1.29ms, 73.5MB)|   통과 (5.64ms, 73.9MB)|
|테스트 18 〉	|통과 (0.44ms, 72.9MB)|   통과 (3.63ms, 77.9MB)|
|테스트 19 〉	|통과 (1.32ms, 75.5MB)|   통과 (5.26ms, 77.8MB)|
|테스트 20 〉	|통과 (0.58ms, 71.7MB)|   통과 (3.58ms, 77.7MB)|

<br>
<br>

- - -

## Reference
-<https://wakestand.tistory.com/419>