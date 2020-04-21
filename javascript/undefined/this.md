# this

> 자바스크립트 this 알아보기

자바스크립트의 this는 고정이 아니며 위치와 호출되는 방식에 따라 달라진다. 여러방식 여러위치에서 써보며 차이를 알아본다.



> 생성자에서 this

가장 이상적인 this의 느낌.. .생성자에서 this는 객체자신을 가리킨다.

```javascript
function Person(name) {
  this.name = name;

  this.getName = function() {
    return this.name;
  }
}

const p1 = new Person('JS');
console.log(p1.getName()); //JS

```



> 호출 방식에 따라 달라지는 this

```javascript
function Person(name) {
  this.name = name;

  this.getName = function() {
    return this.name;
  }
}

const getName  = p1.getName;
console.log(getName()); //??

```

getName 함수를 변수에 담고 호출한다.  getName 는 this.name 을 return 하지만 위와 다른 결과가 나온다.  getName을 호출하는 곳은 글로벌\(window\)이고 this 호출하는 놈을 따라가기 때문에 getName은  window.name을 출력한다. 그래서 누가 호출했는지 잘 살펴봐야한다. 

