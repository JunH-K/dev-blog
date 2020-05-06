# 클래스 \(Class\)

자바스크립트는 프로토타입기반 객체지향언어이다. 기존에 class 라는 것은 없었으며  class 키워드가 생기고 클래스를 정의하는 방법이 생겼다.

> 자바스크립트 객체 정의하기

class 키워드 없이 구현하

```javascript
function Person(name) {
  this._name = name;
}

Person.prototype.getName = function() {
  return this._name;
}

const person = new Person('JS');
console.log(person.getName());

```

멤버변수로 \_name 선언하였고, getName 메서드를 구현하였다.



> 자바스크립트 class 정의하기

```javascript
class Person {
  constructor(name) {
    this._name = name;
  }

  getName() {
    return this._name;
  }
}

const person = new Person('JS');

console.log(person.getName());

```

자바와 같이 class로 정의하며 직관적이다.

