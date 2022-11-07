---
layout: single
title:  "Programmers Coding Test Level 1 - 짝수와 홀수를 구분"
---



Programmers Coding Test Level 1 - 짝수와 홀수를 구분하는 메소드 작성





문제 설명

정수 num이 짝수일 경우 "Even"을 반환하고 홀수인 경우 "Odd"를 반환하는 함수, solution을 완성해주세요.







제한 조건 :

- num은 int 범위의 정수입니다.
- 0은 짝수입니다







 

 

입출력 예:

numreturn

| 3    | "Odd"  |
| ---- | ------ |
| 4    | "Even" |

 

 

```java
class Solution {
    public String solution(int num) {
        
        if(num%2==0){
            return "Even";
        }else{
            return "Odd";
        }
    }
}
```

\

1. if문 사용 ==> num을 2로 나눈 나머지가 == 0 "Even".  아니면  "Odd"

2.판별과 동시에 return;
