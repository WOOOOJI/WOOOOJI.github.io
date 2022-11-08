---
layout: single
title:  "Programmers Coding Test Level 1 - 배열에 있는 데이터로 평균구하기"
---


Programmers Coding Test Level 1 - 평균 구하기.









###### 문제 설명

정수를 담고 있는 배열 arr의 평균값을 return하는 함수, solution을 완성해보세요.

#### 제한사항

- arr은 길이 1 이상, 100 이하인 배열입니다.
- arr의 원소는 -10,000 이상 10,000 이하인 정수입니다.

#### 입출력 예

| arr       | return |
| --------- | :----: |
| [1,2,3,4] |  2.5   |
| [5,5]     |   5    |





```java
class Solution {
    public double solution(int[] arr) {
        double answer = 0;
        
        for(int i=0; i<arr.length; i++){
            answer+=arr[i];
        }
        answer=answer/arr.length;
        return answer;
    }
}
```
1. 배열에 담긴 점수들을 배열의 크기만큼 반복문을 돌려서 answer 변수에 더해서 저장해준다.
2. 구해진 총점 answer값으로 배열의 크기만큼 나눠주면 평균이 나온다.
