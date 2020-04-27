# 프로토타입

> 자바스크립트 프로토타입

자바스크립트 객체는 부모객체를 의미하는 프로토타입 객체가 있고, 자식 객체는 내부적으로 부모객체를 가리키는 내부 프로토타입 링크가 있다. 이 프로토타입을 이용해 상속을 구현한다. 여기서는 프로토타입이 무언인지 알아보려한다. 



> 자바스크립트 객체 생성 방법

* 생성자로 객체 생성

```javascript
function Language(name) {
  this.name = name;
}

const js = new Language('javascript');

console.log(js);

```



* 리터럴로 객체 생성

```javascript
const js = {
  name: 'javascript'
}

console.log(js);

```



두 방법 모두  name프로퍼티가 있고 값도 'javascript'로 같다. 또한 생성된 객체는 내부적으로 부모객체를 가리키는 프로토타입 링크도 있다.

