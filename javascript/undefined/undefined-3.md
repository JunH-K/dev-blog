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



두 방법 모두  name 프로퍼티가 있고 값도 'javascript'로 같다. 또한 생성된 객체는 내부적으로 부모객체를 가리키는 프로토타입 링크도 있다.

여기까지 보면 두 객체는 같아 보이지만 부모객체는 서로 다른 객체를 가리키고 있다.  
결론만 얘기하면 생성자를 통한 객체는 생성자.prototype , 리터럴로 생성한 객체는 Object.prototype을 가리킨다.

{% hint style="info" %}
크롬에서는 \_\_proto\_\_ 프로퍼티로 부모객체를 참조 할 수 있다.
{% endhint %}

```javascript
const js = {
  namd: 'javascript'
}

console.log(js.__proto__ === Object.prototype); //true
```

```javascript
function Language(name) {
  this.name = name;
}

const js = new Language('javascript');

console.log(js.__proto__ === Language.prototype); //true
```

생성자를 통한 객체생성은 당연히 생성자.prototype을 가리키고 리터럴 생성방은 다음과 같다고 할 수 있다.  

```javascript
const preJs = {
  name: 'javascript',
}

const js = new Object();
js.name = 'javascript';


console.log(preJs.__proto__ === js.__proto__); //true

console.log(preJs.__proto__ === Object.prototype); //true
console.log(js.__proto__ === Object.prototype); //true


```

프로토타입의 핵심은 두가지가 있다고 생각한다.

1. 프로토타입 체인
2. 프로토타입 프로퍼티 공유 

> 프로토타입 체인

객체의 변수나 메소드를 사용할때 검색하는 메커니즘이다. 해당 객체에 프로퍼티가 없으면 부모객체를 차례대로 올라가며 검색한다.

```javascript
Object.prototype.getName = function() {
  return this.name;
}

function Language(name) {
  this.name = name;
}

const js = new Language('javascript');

console.log(js.getName());
```

* js.getName\(\) 메서드 호출한다.
* js 객체에 getName이 있는지 찾는다.
* js객체에 getName 없는것을 확인한다.
* Language.prototype 객체에 getName 이 있는지 찾는다. 
* Language.prototype 객체에 getName이 없는것을 확인한다.
* Object.prototype 에 getName 을 찾아 메서드를 실행한다.
* 메서드를 실행하는 객체는 js객체 이므로 this는 js이다.
* return js.name 



> 프로토타입 프로퍼티 공유

같은 생성자로 생성된 객체들은 같은 부모객체\(prototype\)를 가르키기 때문에 prototype 객체에 프로퍼티를 추가한다면 모든 자식에서 접근가능하다.



