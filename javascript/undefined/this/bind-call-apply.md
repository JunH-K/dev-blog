# bind, call, apply

동적으로 바뀌는 자바스크립트 this를 고정으로 바인딩해주는 함수들이다. this 어떻게 고정하고 쓰는방법을 한번 알아보자. 

* call
* apply
* bind

> Function.prototype.call

```javascript
const obj = {
  lang: 'java'
}

function getLang(params) {
  console.log(params); // call 함수의 두번째 파라미터 값
  return this.lang;
}

console.log(getLang()); //undefined
console.log(getLang.call(obj, 'script')); //java

```

첫번째 콘솔은 undefined를 출력한다. 왜냐하면 getLang 내부 this는 브라우저기준으로 window 객체이다. 여기서 또 this가 왜 window냐고 묻는다면 -&gt; [여기를 참조](./)

여기서 getLang 내부의 this를 특정 객체로 바꾸고 싶을때 call 함수를 사용한다. call은 Function.prototype에 존재 하기 때문에 억지로 prototype을 바꾸지 않는한 함수객체만 사용할 수 있다.

call 첫번째 매개변수로 this를 지정할 객체를 전달하고 두번째 매개변수 부터는this를 바 함수의 매개변수로 전달한다.

