---
layout: single
title: "Jason-server 와 Fetch API"
categories: "js_practice"
tag: [JS, 제로베이스프론트엔드스쿨]
toc: true
author_profile: true
#sidebar:
#  nav: "docs"
---

# jason server 와 fetch



본격적으로 javascript과제를 하기에 앞서 토이20 프로젝트 강의를 듣기 시작 했다. 

역시나 지금까지 코딩 테스트에 사용 했던 것과는 다른 부분.. 즉 나한테 아직 생소한 DOM , EVENT , 등이 나왔다. 

하나 하나 차근차근 익히기로 하고 우선 시작은 jason-server 와 fetch로 정했다.



## jason server

 강의에서 jason server와 연결을 하는데 사실 왜 하는건지 몰라서 따로 유튜브를 찾아 봤다. 

 jason server는 쉽게 말해 가짜 서버다. 



- 백앤드 개발자가 아직 서버 개발을 완료 하지 못했을 경우 테스트를 할 수 없기 때문에 json-server 같은 가짜 서버를 이용해서 프론트엔드 스스로 테스트를 해 본다. 
- json-server를 이용해서 프론트앤드 개발을 해 두고 나중에 백앤드 API가 완성이 되면 완성된 API 주소로 바꾸기만 하면 된다. 

- db.json 파일이 '데이터 베이스' 역할을 해준다. db.json의 자료는 서버에 등록 된 데이터 처럼 프론트 앤드에서 가져와서 사용하게 된다.. 

 

​	https://github.com/typicode/json-server



​	제이슨 서버를 위 링크에 나온대로 설치를 한 뒤

​	터미널에 json-server --watch db.json 을 입력하면 실행이 된다. 

 

​	jason generator 사이트를 통해 더미용 jason 데이터를 얻을 수 있다. (필요 없는데이터 빼고 _id -> id로 바꾸고 key값 편한대로 바꾸거나 추가해서 더미로 쓰면 됨) 



프론트 엔드 독자적으로 개발을 계속 할 수 있게 도와주는 것 이다. 





------

## fetch



 사실 fech에 대해서는 JS 수업때 배웠다. 그런데 사실 수업때 한번 듣고 넘어 가면 절대 다시 기억이 안난다. 직접 사용을해 봐야 기억이 난다. 



-  fetch는 비동기 적으로 '서버'와 통신 할 때 사용 한다.

 

https://developer.mozilla.org/ko/docs/Web/API/Fetch_API



새로고침 없이 부분적으로 데이터를 가져 올 수 있다.



<사용법>



\- fetch api의 response는 실제 json 이 아니다.

\- 따라서 fetch api에서는 추가 메서드를 호출해 응답 본문을 받을 필요가 있다. (`.json()`)

 \- axios는 이 과정을 자동으로 해주기 떄문에 바로 response를 받을 수 있다.

\- body 데이터 타입은 헤더의 content-type 헤더와 일치해야 한다.

 

\```

var url = 'https://example.com/profile';

var data = {username: 'example'};

 

fetch(**url**, {

 method: 'POST', // or 'PUT'

 body: JSON.stringify(data), // data can be `string` or {object}!

 headers:{

  'Content-Type': 'application/json'

 }

})**.then**(res => res.json())

.then(response => console.log('Success:', JSON.stringify(response)))

.catch(error => console.error('Error:', error));

\```

 

**.then()** -> 응답이 끝나면 () 안의 내용을 실행 시켜라 (비동기로 실행)



해당 부분은 그냥 그대로 가져다가 쓰면 된다고 한다. 

------

서버와 통신하는 많은 방법이 있겠지만 당분간 fetch를 이용해서 공부를 할것같다. 
