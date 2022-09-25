---
layout: single
title: "코딩 테스트 스터디 1회차"
categories: "cording_test_study"
tag: [JS, 제로베이스프론트엔드스쿨]
toc: true
author_profile: true
#sidebar:
#  nav: "docs"
---

# 코딩테스트 스터디 1회차 leetcode 83 88 7

스터디 그룹에 들어갔다.

​ 원래 8월에도 스터디 그룹에 필수로 참여 했어야 하는데 그걸 모르고 건너 뛰었다. 아직 자바스크립트 공부도 다 하지 못했는데 이미 다른 사람들은 react나 typescript로 스터디를 하길래........ 와... 난 좀더 공부 한 다음 스터디를 해야겠다 라는 생각에 8월 스터디는 필수인데도 불구하고 (필수인지 진짜 몰랐음) 스킵했고 9월에 코딩테스트 스터디를 시작 했다.

​ 매주 코딩테스트를 통해 일정 점수 이상을 받아야 하는데 아직 힘들다...

---

## 83. 연결리스트 (Linked List) 문제

leetcode easy 83번 문제.

head를 받고 element 중복 제거하기.

```javascript
var deleteDuplicates = function (head) {
  let cur = head;

  while (cur) {
    if (cur.next !== null && cur.val === cur.next.val) {
      cur.next = cur.next.next;
    } else {
      cur = cur.next;
    }
  }
  return head;
};
```

사실 이 문제는 혼자 못풀었고 다른 사람의 풀이를 참고 한 다음 다시 풀었다.

노드의 next를 바꿔주면 되는 간단한 문제 인데 머리로는 이해했고 코드를 보고도 이해 했었다. 그런데 막상 직접 코드를 작성 하려니 시작을 어떻게 해야 할지 감이 잘 안왔다. 연결리스트 문제는 처음이라 그런가 ?? 실제로 테스트에선 잘 안나온다던데..

---

## 88. 배열 두개 합하기

```javascript
var merge = function (nums1, m, nums2, n) {
  for (let i = 0; i < n; i++) {
    nums1.push(nums2[i]);
  }

  nums1.sort(function (x, y) {
    return x - y;
  });

  for (let i = 0; i < m + n; i++) {
    if (nums1[i] === 0) {
      nums1.splice(i, n);
      break;
    }
  }
  return nums1;
};
```

두 배열을 합하고 첫번째 배열에 추가로 들어있는 n개 만큼의 0을 제거 하는 문제다.

난 우선 두 배열을 합했고 오름차순으로 정렬을 한 다음 n개 만큼의 0 을 제거 했다. nums1 에서 미리 0을 다 제거하고 두 배열을 합하는 방법도 있다. (이게 더 깔끔)

그런데 문제를 잘 보면 'The final sorted array should not be returned by the function' 이란 말이 있는데 정확히 이게 뭘 의미하는지 모르겠다. return으로 배열을 반환하지 말란건가 ??

여튼 풀이를 보니 nums1의 요소와 nums2의 요소를 하나하나 비교 해서 nums1에 nums2의 요소를 하나하나 집어 넣었다. 그렇게 푸는게 코드가 길어지고 좀 복잡해 지지만 어렵진 않다.

이건 풀고 나서도 찜찜...

---

## 7. 정수 뒤집기

```javascript
var reverse = function (x) {
  let num = Math.abs(x);
  let arr = [];
  let result = 0;

  while (num >= 1) {
    arr.push(num % 10);
    num = Math.floor(num / 10);
  }

  arr = arr.join("");

  if (x >= 0) result = Number(arr);
  else if (x < 0) result = Number(arr) * -1;

  if (result >= 2 ** 31) result = 0;
  else if (result < -1 * 2 ** 31) result = 0;

  return result;
};
```

주어진 수를 반대로 reverse 시키는 문제다.

보통 이런 문제는 숫자 -> 문자열 - > 배열 -> reverse -> 문자열 -> 숫자 방식으로 풀었었는데 이번에는 그렇게 말고 나머지를 이용해서 풀고 싶었다. 그런데 숫자를 이용해서 다 나눈다음에 그냥 문자열로 만들고 다시 숫자로 만들었다. ㅋㅋㅋㅋ

계속 숫자로 풀어내려면 다 쪼개어낸 수를 뒤에서부터 1 ,10 ,100 ,1000 씩 곱해서 더해줘야 하는데 어쩌다보니 그냥 문자열로 만들어 버렸다. 즉 숫자로풀기 + 문자열로 풀기 두가지가 섞인거...

이래푸나 저래푸나 뭐.. 크게 차이는 없는거 같은데 문자열로 바꿔서 푸는게 더 짧다.

그래도 숫자로만 푸는 법을 알고 있는건 좋을듯.
