# 프로그래머스 Level1 : 연습문제 직사각형 별찍기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12969)

```java
import java.util.Scanner;

class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();

        for(int i=0; i<b; i++){
            for(int j=0; j<a; j++){
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```