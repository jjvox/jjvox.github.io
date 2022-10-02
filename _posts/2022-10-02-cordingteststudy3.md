---
layout: single
title: "코테 스터디 3회 / leetcode 11번 101번 104번"
categories: "cording_test_study"
tag: [JS, 제로베이스프론트엔드스쿨]
toc: true
author_profile: true
#sidebar:
#  nav: "docs"
---

# 코딩테스트 스터디 3회차 leetcode 11 101 104



##  104. 이진트리 깊이? 구하기 - easy

```javascript
var maxDepth = function(root) {
    
    let count = 0;
    let maxnum = 0;
    
    let maxdepth = function(root) {
        if(root === null) {
            if (maxnum < count) {
                maxnum = count;    
            }
            return;
        }
        count++;
        maxdepth(root.left);
        maxdepth(root.right);
        count--;
    }
    
    maxdepth(root);
    
    return maxnum;
};
```



  열심히 풀었는데 알고보니 공식이 존재했다...  

 공식같은거 잘 모르는 사람이라.. 열심히 풀었다. 왼쪽부터 null 값이 나올 때 까지 count 하며 내려 갔다가 null 값을 만나면 오른쪽 노드로 가고 둘다 null 값이 나왔을경우 count-- 를 해주고 그 윗 노드로 다시 올라가는 식으로 max값을 찾아 업데이트 해줬다.





------

## 101.  대칭 트리 - easy

```javascript
var isSymmetric = function(root) {
    if (root === null) {
        return true;
    }
    
   let sym = function(left, right) {
        if (left === null && right === null) return true;
        if (left === null || right === null) return false;
        if (left.val !== right.val) return false;
        
        return sym(left.left, right.right) && sym(left.right, right.left);
    }
    return sym(root.left, root.right)
};
```



 노드의 root를 기준으로 좌 우가 대칭이 되는지 확인하는 함수를 만들어야 한다. 

이전에 트리 문제에서 항상 이용 해 왔던 재귀를 이용해서 문제를 풀었다. 

 left 와 right를 따로 계속 탐색하기



------

## 11. 컨테이너에 max로 물 채우기

```javascript
var maxArea = function(height) {
    
    let i = 0;
    let j = height.length-1;
    let max = 0;
    
    while (i != j ) {
        if (height[i] <= height[j]) {
            if(max < height[i]*(j-i)) {
                max = height[i]*(j-i);
            }
            i++;
        } else if (height[i] > height[j]) {
            if (max < height[j]*(j-i)) {
                max = height[j]*(j-i);
            }
            j--;
        }
    }
    return max
};
```



 이 문제는 처음에 이중 for문을 이용해서 풀었다. 그런데 계속 시간 초과가 떴다 ㅜㅜ 

이런저런 조건을 달아서 시간을 줄여 보려 했지만 계속 시간 초과가 떴고 결국 풀이를 봤따....

풀이를 보니 이중 for문을 이용해서 가능한 경우의수를 모두 탐색 하는것도 옳은 방법이긴 하지만 시간 복잡도가 높아서 그 방법 보다는 양쪽 끝 에서 부터 탐색 하는 방법이 추천 되었다. 



 그래서 양쪽 끝 부터 차례대로 가운데로 오는 방법으로 풀었다. 시간 복잡도는  O(n)





------

 짧았던 한달간의 코딩테스트 스터디가 끝났다. 

 첫 주에는 추석이 있어서 스터디를 하지 못했고 2 ~4주까지 3번만 진행 했다. 

 스터디원 한분은 아쉽게도 코딩테스트에서 탈락 하셨고 ㅜㅜ 다행히 나머지 4명은 총 12회차에 걸친 코딩 테스트를 모두 통과 했다. 아직 마지막 12회차가 남았지만 지금까지 성적으로도 이미 탈락은 벗어 난 상태이다. 



 자바스크립트로 코딩테스트를 혼자 공부하기엔 자료가 부족해서 힘 들었는데 이제 코딩테스트는 잠시 내려 두고 자바스크립트 구현과 타입스크립트 공부를 해야 겠다. 자바스크립트를 이용해서 문제나 풀줄 알지 html과 연동해서 실제로 구현 시키는 법은 전혀 모른다 ... 이제 코테 보다 자바스크립트 구현에 집중하고 자바스크립트 과제를 해야겠다. 



 요즘 기업들이 필수로 코딩테스트를 본다던데 우선 자바스크립트로 해보고 안되면 나중에 파이썬을 배워야 겠다. 
