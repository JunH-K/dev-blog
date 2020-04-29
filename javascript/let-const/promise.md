---
description: Javascript Promise
---

# Promise

자바스크립트에서 비동기 처리시 사용하는 프로미스를 알아본다. 자바스크립트에서 비동기 처리 로직을 프로미스를 이용해 콜백패턴대신 쉽게 패턴화해서 구현할 수 있다. 



> 프로미스 API 기본 사용법

* 프로미스 생성자를 이용하여 프로미스 객체생성

```javascript
const promise = new Promise((resolve, reject) => {
  // 비동기 처리
  // 처리가 끝나면 resolve, reject을 호출
});

```

* 처리가 성공적으로 되면 promise 객체의 then메서드의 콜백함수로 등록한 함수가 호출된다. 간단한 예제를 살펴보자.

```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
   resolve('타임아웃');
  }, 1000);
});

promise.then((value) => {
  console.log(value); //타임아웃
});
```

resolve 인자로 전달된 값이 promise.then 콜백함수 인자로 전달된다.

