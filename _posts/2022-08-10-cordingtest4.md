---
layout: single
title: "코딩 테스트 4회차"
categories: "cording_test"
tag: [JS, 제로베이스프론트엔드스쿨]
toc: true
author_profile: true
#sidebar:
#  nav: "docs"
---



## 코딩테스트 4회차 (2022-08-10)  



| 날짜       | 회차 | 점수 |                                                              |
| ---------- | ---- | ---- | ------------------------------------------------------------ |
| 2022-07-20 | 1    | 0    | 처음 해보 테스트.. 하나도 못풀었다.                          |
| 2022-07-27 | 2    | 3    | 난이도가 조정되었다. 처음으로 3문제를 풀었다.                |
| 2022-08-03 | 3    | 5.4  | 2회차와 비슷한 난이도. 완전히 다 맞진 못해도 건들여 볼 수 있는게 늘었다. |
| 2022-08-10 | 4    | 3    | 난이도가 올랐다. 4점은 받을 수 있었는데 아쉽게 3점...        |



------



### 1번 문제 - 거스름돈 갯수 구하기



내 풀이

```javascript
function solution(A) {

    let result = 0; 
    let krw = [50000, 10000, 5000, 1000, 500, 100, 50, 10, 5, 1];

    for (let i = 0; i < krw.length; i++) {

        if ( A < krw[i]) continue ;

        else {
            result += parseInt(A/krw[i]);
            A = A-(krw[i]*parseInt(A/krw[i]));
        }
    }
 return result
}
```



 화폐를 배열로 만들고 반복문을 통해 가장 큰 50,000원 권 부터 차례대로 뺐다.    

 난 if문을 사용해서 원금이 화폐보다 작을땐 스킵 해줬는데 생각해보니 parseInt를 사용 할 경우 어차피 소숫점이 사라지고 0이 반환 될거라 if문은 굳이 필요 없었던거 같다.   

 

```javascript
else {
            result += parseInt(A/krw[i]);
            A = A-(krw[i]*parseInt(A/krw[i]));

```

 사실 위 코드에서 처음엔 아래와 같이 짰다가 안되서 한참을 헤맸었다.

```javascript
else {
            A = A-(krw[i]*parseInt(A/krw[i]));
            result += parseInt(A/krw[i]);

```

 당연히 A를 새로 할당하고 나서 다시 나누니까 계속 0 만 나왔지...

 왜그런지 한참 고민을 하다가 순서만 바꿔주니 해결! 재할당할때 잘 생각해서 하자.



그리고 나는 원금에서 거스름돈을 계속 빼줬는데 모범 답안을 보니 굳이 빼주지 않고 거스름돈으로 나눈 나머지를 계속 할당했다. 



```javascript
 A %= moneys[i];
```



내 풀이보다 더 심플. 하지만 딱 보자마자 바로 이해하기엔 내 풀이가 더 쉬울거 같긴 하고.. 



------

### 3번 문제 - 조건을 만족하는 정수 구하기

내 풀이

```javascript
function solution(N, K) {
let arr = [];

    if (N>=0) {
        arr = N.toString().split("");

        for (let i = 0 ; i < arr.lenght; i++) {
            if (arr[i] < K) {
                arr[i] = K;
                break;
            }
        }
    }else {
        arr = N.toString().split("");
        for (let i = 1 ; i < arr.length; i++) {
            if (arr[i] > K) {
                arr[i] = K;
                break;
            } 
        }
    }
    return arr.join("")
}
```



시간을 한참 잡아먹었던 문제다. 

식은 금방 세웠는데... 왜 안되지 왜안되지... 그렇게 계속 식만 뜯어 고치다가 시간이 지나서 0점 처리됐다.. 그리고 오기가 생겨서 계속 봤는데 이럴수가..

```javascript
arr.length 라고 써야 했는데
arr.lenght 라고 오타가 나있었다..
```



하 오타... 이제 한달 남짓 공부를 했고 내가 짠 코드가 확실하다는 자신이 부족 하기 때문에 실행이 안 될 경우 코드 부터 수정 하려고 한다. 그런데 오타 때문이었다니..  

 공부 초창기엔 오타가 거의 없었다. 영타도 안익숙하고 코딩 자체도 안익숙 하다보니 하나하나 천천히 타자를 쳤지만 이제 좀 익었다 라는 생각에 빨리 타자를 치다보니 오타가 슬슬 나기 시작한다.

 다시 천천히 꼼꼼히 작성 해야겠다. 오타가 정말 위험하구나..



해당 문제의 경우 아무리봐도 난 모범 답안보다 내 풀이가 나은것 같다.

모범 답안은 좀더 정석적으로 메소드를 활용해서 더 있어보이긴 하지만..



------

### 8번 문제 - 둘레가 가장 큰 사각형의 둘레를 구하기

내 풀이

```javascript
function solution(arr) {

    arr.sort(function (x, y) {return x - y;});

    if (arr[arr.length-1] >= arr[arr.length-2] + arr[arr.length-3] + arr[arr.length-4]) {
        return 0
    } else {
        return arr[arr.length-1] + arr[arr.length-2] + arr[arr.length-3] + arr[arr.length-4]
    }
}
```



 배열이 주어지면 그 배열 내의 정수를 활용해서 가장 큰 사각형을 만들면 된다.

 배열을 오름차순이든 내림차순이든 정렬 한 다음 가장 긴 숫자들만 모으면 된다. 하지만 한변이 나머지 세변의 길이보다 길거나 같을 경우 사각형은 완성되지 못하기 때문에 해당 경우의 조건만 넣어주면 된다. 

 지금보니 난 오름차순으로 정리를 했는데 (오름차순이 좀 더 익숙한가보다.) 내림차순으로 정렬 한 다음 [0] 부터 [3] 까지 더 하면 된다. 

 한번만에 풀었음!  그래도 매주 한번만에 푸는 문제가 나오긴 한다.



------

### 9번 문제 - 대푯값의 합의 최솟값을 구하기

내 풀이

```javascript
function solution(arr) {
    let result = 0;
    arr.sort(function (x,y) {return x-y;});

    for (let i = 1 ; i <= arr.length/2; i++) {
        result += arr[2*i-1];
    }
    return result; 
}
```



 2N 개의 정수가 주어질 때, 주어진 정수를 2개씩 그룹 짓고 그중 큰 값의 합이 가장 적을 때를 구하는 문제다. 

 배열에 무작위로 정수가 들어 있기 때문에 그냥 그룹을 지을 경우 큰수들이 대푯값으로 지정 될 수가 있다. 대푯값이 가장 적어 지려면 작은 수부터 차례대로 그룹을 지어야 한다. 

 그래서 오름차순으로 배열을 정리 한 다음 짝수번째(2개로 묶음) index로는 홀수에 해당하는 수들의 합이 대푯값의 합이 가장 적어지는 경우다. 



해답지엔 뭐 복잡하게 적어뒀떤데...

아직 난 모르는 메소드가 너무 많은거 같다. ㅎㅎㅎ ..



------



 다음 5주차 테스트 부터는 10문제중 5문제를 맞춰야 한다. 안그러면 탈락...  

 자바스크립트를 좀더 공부하고 자료구조, 알고리즘을 하고 싶었으나 어쩔 수 없이 이번주엔 자료구조, 알고리즘 문제풀이에 집중 해야겠다. 만들고 싶은 홈페이지가 있지만 우선은 코딩 테스트를 위해 자료구조, 알고리즘 공부에 좀더 매진 할 예정.   

 그리고 짧고 간단하고 보기 쉬운 코드가 좋은건가 아니면 메소드를 많이 쓰고 혹시 모를 변수를 대비해 여러 조건이 붙은 코드가 좋은건가 궁금하다. 