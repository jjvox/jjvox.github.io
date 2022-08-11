---
layout: single
title:  "3회차 코딩 테스트"
summary: 3회차 코딩테스트
author: jjvox
date: '2022-08-07'
---

<h3> 3회차 코딩테스트 </h3>

 <div>
 <p> 1회차때 하나도 못풀고 2회차때 3점을 얻었고 이번 3회차 에선 5.4점을 얻었다. </p>
 </div>

<div> 
 <h4> 첫번째 문제. 문자열 역으로 출력하기. </h4>
 <p> 배열로 바꿔 쪼갠 다음 다시 합했다. </p>
  <p> 그러나 다른사람 답안지를 보니.. 정말 쉽고 깔끔하게 해결 했더라 ㅜㅜ </p>

```js
function solution(s) {
   var answer = '';   

   s = s.split("");
   s = s.reverse();

	for ( let i = 0 ; i < s.length; i ++){
    answer += s[i];
	}
    
 return answer;
}
```
   

  <div>
  <h4> 두번째 문제. 규칙을 만족하는 a,b 쌍의 갯수 출력 </h4>
    <p> 나쁘지 않게 푼거 같다. 그러나 역시 다른 사람 풀이를 보면 정말 다들 기발하다. </p>

   

```javascript
function solution(nums) {
    var answer = 0;

	for ( let i = 0; i < nums.length; i++) {
   	 for ( let j = i; j < nums.length; j++) {
        if (i == j) {
            continue;
        } else if (nums[i] == nums[j]) {
            answer++;
        } 
     }
	}
 return answer;
}
```


  <div>
      <h4> 세번째 접두사 갯수 출력 문제... </h4>
       <p>시간을 엄청 잡아 먹었고 0.6점 밖에 획득하지 못했다. ㅜㅜ </p>

​      


```javascript

function solution(array, s) {
 var answer = 0;

 s = s.split("");
 let answer2 = 0;

	for ( i = 0; i <= 100; i++) {

   	 if (array[i]==undefined) break;

   	 let j = array[i].split("");

  	  for ( let t = 0; t < j.length; j++) {
       if (j[t]===s[t]) {
           answer2++;
       }     
       if(answer2 === j.length) {
       answer++;
       }
   	  }         
    }
  return answer;
}
```
​    다른 사람들코드를 보니 startswitch 메소드를 썼던데 난 그게 뭔지 몰랐따.. 아직 공부할게 많구만..
​    



  <div>
  <h4> 네번째 문제. 일치하는 단어의 인덱스를 반환하기 </h4>
  <p> 이것도 다 풀지 못했다. </p>

  


```javascript
function solution(sentence, word) {
    var answer = 0;

	sentence = sentence.split(" ");
	answer = sentence.indexOf(word);

	return answer;
}
```
  

  뭐가 문제인지 아직 잘 모르겠다.





  <div>
    <h4> 다섯번째. nums 내에 n과 일치하는 숫자 중 가장 작은 index를 반환</h4>
    <p> 갈수록 난이도가 올라 갈줄 알았는데 갑자기 다섯번째에 말도안되는 쉬운문제가 ?? </p>
    <p> 한번에 고민없이 2분만에 완료. 코드가 머릿속에 확실히 있으니 한번에 풀어지는 신기한? 경험을한 첫 문제다. ㅋㅋ </p>



```javascript
function solution(nums, n) {
    var answer = 0;
	answer = nums.indexOf(n);

	return answer;
}
```

  

  <div>
  <h4> 여섯번째. 규칙을 만족하는 쌍 찾아내기. </h4>
  <p> 이중 for문을 사용하는거 까진 했으나 if문 조건을 잘 못만들었다. </p>




```javascript
function solution(nums, d) {
    var answer = 0;

	for (let i = 0 ; i < nums.length; i++) {
   	 for (let j = i+1; j < nums.length; i++) {
        if (i==j) break;
        else if (nums[i]==nums[j]) {
            nums[i]%d 
      	}
   	 }
	}
 return answer;
}
```



  <div>
    <h4> 일곱번째. 내가 일곱번째 문제까지 읽어보다니... </h4>
    <p> 물론 앞에 문제를 다 맞추며 온건 아니지만 제한 시간내에 읽어보고 고민해보고 할수 있는데까진 다 해보고 여기 까지 왔다는게 기뻤다. </p>
    <p> 첨엔 이렇게 까지 할 줄 모르고 여유롭게 풀다가 막판엔 정말 초단위로 빠르게 풀기 시작 했다. ㅋㅋ 그래서 마지막 문제는 급하게 이것저것 시도만 해봄 </p>


```javascript

function solution(array, p) {
var answer = 0;

 for ( let i = 0; i<=100; i++) {
    if (array[i] == undefined) break;

    let arr = array[i];
    let arr_2 = arr.split("");

    if (arr_2[0] == p) {
        answer++;
    }
 }

 return answer;
}
```

​    접두사 가지는 배열을 찾아내는건데 앞에서 나온 접두사 문제와 마찬가지로 잘 못풀었다. 이부분 공부 다시 필요.





  <div>
    <p>
      아직 자바스크립트가 익숙하지 않고 자료구조및 알고리즘 공부 자체를 다 하지 못했다. 
    우선 크게 한번 다 보고 부족한부분 집중해서 보는 식으로 공부를 해야겠다. 첨부터 꼼꼼히 하나하나 익히며 하려다보니 테스트를 따라 갈수가 없다.
    이제 그래도 처음 접했을때의 아무것도 모르겠던 상황은 지났으니 좀더 공부에 속도가 붙을 것 같다.
  </p>
  <p>
    그리고 지금까지 네이버 블로그에 계속 코딩 공부와 테스트에 관한 글을 써왔다. 그런데 개발자들은 또 네이버 블로그를 안쓴다고 하네 ?? 
    velog, notion, tstory, github 를 많이 쓰는거 같았는데 그중에 그래도 가장 글로벌 하고 많이 쓰는 github로 선택. 
    10년 넘게 네이버 블로그를 쓰다보니 네이버가 제공해주는 툴에 익숙해 졌는데 github는 완전 자유지만 그만큼 모든걸 직접 해야해서 더 힘들었다..
    블로그를 만드는거 자체도 힘들다니 ㅋㅋ 그래도 공부 해둔 html 마크업 언어를 복습할 겸 이걸로 써봐야겠다.
    지금은 겨우 블로그 만들고 글 하나 쓰는게 전부지만 이제 보기 좋게 좀 꾸미고 공을 들여 봐야지 
  </p>
  </div>

​    

#제로베이스프론트엔드스쿨 #제로베이스
