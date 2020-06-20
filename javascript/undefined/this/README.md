# this

> 자바스크립트 this 알아보기

자바스크립트의 this는 고정이 아니며 위치와 호출되는 방식에 따라 달라진다. 여러방식 여러위치에서 써보며 차이를 알아본다.



### 생성자에서 this

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



### 호출 방식에 따라 달라지는 this

```javascript
function Person(name) {
  this.name = name;

  this.getName = function() {
    return this.name;
  }
}

const p1 = new Person('JS');
const getName  = p1.getName;
console.log(getName()); //??

```

getName 함수를 변수에 담고 호출한다.  getName 는 this.name 을 return 하지만 위와 다른 결과가 나온다.  getName을 호출하는 곳은 글로벌\(window\)이고 this는 호출하는 놈을 따라가기 때문에 getName은  window.name을 가리킨다. 그래서 누가 호출했는지 잘 살펴봐야한다. 

위 근거를 확인하기 위해 다른 예제를 살펴보면

```javascript
function Person(name) {
  this.name = name;

  this.getName = function() {
    return this.name;
  }
}

const p1 = new Person('JS');
const getName = p1.getName;

const obj = {
  name: '안녕'
}

obj.getName = getName;
console.log(obj.getName()); //안녕 

```

getName을 obj 프로퍼티로 추가한 후 obj.getName을 호출한다. 위에 논리대로 누가 호출했냐에 따라서 this는 바뀌기 때문에 obj가 getName을 호출하게 되고 this -&gt; obj   obj.name 값이 출력된다.

### 일반 함수에서 this

```javascript
function Person(name) {
  this.name = name;

  this.getName = function() {
    return this.name;
  }
}
```

위 함수를 new 키워드로 호출하면 생성자로 작동하고 그냥 호출하면 일반함수로써 호출된다. 일반 함수로호출되면 this가 의미가 없어진다. 왜냐하면 누가 호출하냐에 따라 달라지기때문에 생성자로 쓰일때 this 가  작성의미 대로 쓰일 수 있다.

결론은 this는 고정이 아니라 어디에서 쓰는지 누가 호출했느냐에 따라 달라지는것을 알고 있어야한다.

### 콜백 함수의 this

콜백함수에서 this는 또 달라진다.

```javascript
const obj = {
  language: 'javascript',
  getLanguage: function() {
    console.log(this.language); //javascript
    setTimeout(function() {
      console.log(this.language); //undefined
    }, 0);
  }
}

obj.getLanguage();

```

객체내부에서 this키워드는 객체자신을 가리킨다. 하지만 콜백함수에서 this는 객체자신을 가리키는것이 아니라 위에서 보았듯이 누가 호출했냐에 따라 달라지기 때문 콜백함수의 this는 브라우저기준 window로 바뀌면서 undefined가 출력된다.  




