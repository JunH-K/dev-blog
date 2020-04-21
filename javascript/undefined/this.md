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

