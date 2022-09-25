---
layout: single
title: "코테 스터디 2회 / leetcode 8번 94번 100번"
categories: "cording_test_study"
tag: [JS, 제로베이스프론트엔드스쿨]
toc: true
author_profile: true
#sidebar:
#  nav: "docs"
---

# 코딩테스트 스터디 2회차 leetcode 8 94 100



 두번째 코딩테스트 스터디를 가졌다. 이번에는 leetcode 뿐만 아니라 코딩테스트 문제에 대해서 같이 풀이를 했다. 

2달 넘게 혼자 공부하다가 같이 공부를 하는 동지가 생겨 너무 좋고 또 다른사람 풀이를 설명까지 들으며 직접 볼 수 있어서 더 좋다. 

신기하게도 전부 다 다른 스타일로 문제를 접근한다. ㅋㅋ 각자 편한 방법으로 !! 배열, 객체, map 등등 ㅋㅋㅋ  



------

## 94. 이진트리 중위 순회 - easy

​	알고리즘 중 이진트리를 중위 순회 하는 문제다! 

 강의에서 배운대로 재귀함수를 사용해서 문제를 풀었다. 함수 자체는 어려울게 전혀 없었는데 leetcode 사용법? 을 몰라서 좀 헤맸다. 내가 코드를 첨부터 다 짜는게 아니라 이미 node들이 등록 되어 있어서 딱 문제에서 말하는 부분만 구현 하면 됐는데 내가 함수 밖에 변수를 선언해서 계속 꼬였다. leetcode 문제는 주어진 함수 내부에서만 문제를 푸는걸로...



```javascript
var inorderTraversal = function(root) {
    
    let number = [];
    
    let traversal = function(root) {
        
        if(root === null) {
        return;
        }
        
        traversal(root.left);
        number.push(root.val);
        traversal(root.right);
     
        return;   
    }
    traversal(root);
    return number; 
};
```



 재귀를 통해 null이 될때가지 탐색을 한 다음 차례차례 올라오며 값을 push 해줬다.

그냥 알고리즘 배운거 복습 정도! 



------

## 100.  주어진 이진트리가 같은지 비교하기 - easy

 두번째 문제도 이진트리다.  주어진 이진트리가 같은지 비교하는 문제! 

간단 할 줄 알았으나 예외 처리 해야 할것들이 좀 있어서 사실 다른 사람의 풀이를 살짝 확인 했다. ... 

풀이 맥락은 같았으나 추가 조건을 더 달아줬다. 



```jade
var isSameTree = function(p, q) {
    
    let sameTree = function(p, q) {
    
        if(p == null && q == null) return true;
        if(p != null && q == null) return false;
        if(p == null && q != null) return false;
        if(p.val != q.val) return false;
        
        if(p.val == q.val) {
            
            return (sameTree(p.left, q.left) && sameTree(p.right, q.right));
        }
    }
    return sameTree(p,q)
};
```



두 트리가 같으면 true 다르면 false를 반환한다. 둘다 null값을 가지면 true를 반환하고 한쪽은 null인데 한쪽은 값을 가진다면 false를 반환한다. 한번만 서로 다른 케이스가 나와도 false를 반환 하면 되고 둘다 값을 가지면서 같을 경우 다시 탐색을 해준다. 



 위에서 풀었던 재귀 방식으로 이 문제 도 풀었다. 





------

## 8. 문자열을 정수로.. 엄청난 하드코딩을 했다. - medium

 

 이 문제는 풀긴 풀었으나 못풀었다고 해도 될거 같다. 

 문제에 주어진 조건이 너무나 많았고 코드를 실행 할 때 마다 새로운 반례에 의해 실패가 뜨길래 그렇게 나온 반례들을 전부 조건으로 예외 처리 해줬다.. 즉 노가다 하드코딩으로 푼 문제 ㅜㅜ. 풀다가 중간에 "아 이렇게 푸는건 아닌데 " 싶었지만 오기로 이 방식으로 해보고 싶어서 끝내 풀었다. 무려 3시간 30분간 ㅋㅋㅋㅋ

 근데... 다른 분들은 단 몇줄만에 풀었던........ ㅜㅜ



```javascript
var myAtoi = function(s) {
    
    let arr = s.split("")
    let arr_result = [];
    let result = 0;

    for(let i = 0; i < arr.length; i++) {

        if (!isNaN(arr[i])) {

            arr_result.push(arr[i])

            if (Number.isInteger(parseInt(arr[i])) && arr[i+1] == " ") break;
            if (Number.isInteger(parseInt(arr[i])) && arr[i+1] == "-") break;
            if (Number.isInteger(parseInt(arr[i])) && arr[i+1] == "+") break;
        } 

        if (isNaN(arr[i])) {
            if (arr[i] == '-' || arr[i] == '+') {
                if (arr[i+1] == '-' || arr[i+1] == '+') break;
                if (arr[i+1] == ' ') break;
                if (isNaN(arr[i+1])) break;
                arr_result.push(arr[i]);
            }else break;
        }
    }

    if (parseInt(arr_result.join("")) > Math.pow(2,31)-1){        
        result = Math.pow(2,31) -1
    } else if (parseInt(arr_result.join("")) < Math.pow(-2,31)) {
        result = Math.pow(-2,31)  
    } else {
        result = Number(arr_result.join(""));
    }
  return result
}

```



trim () 라는 처음 보는 메서드인데 문자열의 공백을 전부 제거 해 준다고 한다. 

이런 메서드들좀 익혀 둬야지.. 
