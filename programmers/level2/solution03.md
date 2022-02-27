# 프로그래머스 Level2 : 위클리 챌린지 전력망을 둘로 나누기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/86971?language=java)

```java
import java.util.Queue;
import java.util.LinkedList;

class Solution {
    //(루트 송전탑, 끊어진 전선 번호(index), 전체 전력망)
    private int sizeOfTree(int root, int cut, int[][] wires){        
        Queue<Integer> queue = new LinkedList<>();
        int l = wires.length;
        boolean[] check = new boolean[l];   //확인한 전선
        int curr = 0;       // 보고 있는 송전탑
        int size = 0;       // 전력망의 송전탑 갯수
        
        check[cut] = true;
        queue.offer(root);  
        
        while(!queue.isEmpty()){
            curr = queue.poll();
            size++;
            for(int i=0; i<l; i++){
                if(check[i]){
                    continue;
                } else if(wires[i][0]==curr){
                    queue.offer(wires[i][1]);
                    check[i] = true;
                } else if(wires[i][1]==curr){
                    queue.offer(wires[i][0]);
                    check[i] = true;
                } 
            }
        }
        return size;
    }
    
    public int solution(int n, int[][] wires) {
        int answer = -1;
        int l = wires.length;
        int treeSize;
        int abs;       
        
        // wire가 끊어졌을때 생긴 두개의 전력망의 크기
        for(int i=0; i<l; i++){
            treeSize = sizeOfTree(wires[i][0],i,wires);
            abs = Math.abs((n - treeSize)-treeSize);
            
            // 차이가 가장 작은지 확인
            if(answer<0 || answer > abs){
                answer = abs;
            }
        }
        
        return answer;
    }
}
```