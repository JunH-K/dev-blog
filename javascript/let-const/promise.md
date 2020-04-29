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

* 처리가 성공 or 실패가  되면 promise 객체의 then, catch 메서드의 콜백함수로 등록한 함수가 호출된다. 간단한 예제를 살펴보자.

```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
   resolve('타임아웃');
//   reject('실패');
  }, 1000);
});

promise.then((value) => {
  console.log(value); //타임아웃
}).catch((error)=>{
  console.log(error); //실패
});
```

성공했을때 resolve 인자로 전달된 값이 promise.then 콜백함수 인자로 전달된다.  
실패했을때 reject 인자로 전달하면 catch 콜백함수가 호출된다.



* 프로미스 상태 

프로미스 객체를 새성하면 세가지 상태가 있다.

1. Fulfilled : 성공
2. Rejected : 실패
3. Pending : 성공, 실패 전 초기상태

pending 상태로 시작해서 Fulfilled나 Rejected 상태로 끝난다. 고로 promise.then 메서드는 상태가 끝날때 호출될  콜백함수를 등록하는 메서드이다.

* 프로미스 여러개를 한번에 실행하기 Promise.all

```javascript
function timerPromisefy(delay) {
    return new Promise(function (resolve) {
        setTimeout(function () {
            resolve(delay);
        }, delay);
    });
}

var startDate = Date.now();


Promise.all([
    timerPromisefy(1),
    timerPromisefy(32),
    timerPromisefy(64),
    timerPromisefy(128)
]).then(function (values) {
    console.log(Date.now() - startDate + 'ms'); // 총 128ms
    console.log(values); // [1,32,64,128]
});
```

Promise.all 메서드 인자로 배열프로미스를 넣어준다.  
다른 프로미스와 같이 then 메서드로 값을 받을 수 있으며 all메서드로 전달된 배열 순서대로 값을 전달해 준다. 

동시에 프로미스를 실행하기 때문에 가장 오래걸리는 프로미스가 완료되야 then 메서드가 실행된다.

