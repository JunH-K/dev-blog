# 화살표 함수

function 키워드 대신 화살표로 간략한 함수 표현이 가능하다. 익명함수로만 사용가능하고  함수표현식으로 사용한다.

### 화살표 함수 선언방식

function 키워드로 선언하고 화살표 함수로 바꿔보자.

```javascript
  function f() {}
  const f = () => {};
  --------------------
  
  function f(x) {
    return x;
  }
  const f = (x) => {
    return x;
  };
  const f = (x) => x; //return 문 생략가능.
  const f = x => x; //매개변수가 하나라면 괄호 생략가능.
  
  --------------------
  
  function f() {
    return { x: 1 };
  }
  
  const f = () => {
    return { x: 1 };
  };
  
  const f = () => ({ x: 1 }); 
  //return 값이 객체리터럴이라면 소괄호() 로 감싸야 한다.
  
  ---------------------
```

### function 키워드 선언과 차이점

* this

```javascript
function func() {
  console.log(this); //window
}

const arrowFunc = () => {
  console.log(this); //window
}

func();
arrowFunc();
```

위 예제는 콘솔결과는 별차이가 없다. 둘다 window를 가리킨다.  
하지만 함수가 선언된 위치와 호출을 누가 했느냐에 따라 this가 바뀐다.

```javascript
function func() {
  console.log(this);
}

const arrowFunc = () => {
  console.log(this);
}

const obj = {
  func: func,
  arrow: arrowFunc
}

obj.func();
obj.arrow();

```

obj.func 를 호출하면 this -&gt; obj  
obj.arrow 를 호출하면 this-&gt; window 

??????

개발자의 의도대로라면 this가 obj가 나오는게 맞을것이다. 하지만 화살표함수는 그렇지가 않다.  
이것으로 알 수 있는건 객체의 메소드로 쓸수가 없다는것이다. 메소드로 쓰일려면 function 키워드로 선언해서 써야한다. 

그러면 화살표함수는 this를 어떻게 잡는것인가..

다음예제로 살펴보자.

```javascript
const obj = {
  func: function() {
    return () => {
      console.log(this); //??
    }
  },
}

obj.func()();

```

뭔가 억지 스럽긴 하지만 화살표함수까지 호출하게 되면, this는 obj로 잡힌다.  
그 이유는 화살표함수 this는 정적으로 결정되고 그 기준은 함수가 선언된 상위스코프 this 를 참조한다.

화살표함수가 선언된곳 -&gt; obj.func 함수 안 -&gt; func 함수안의 this - &gt; obj   
고로 화살표함수 안의 this는-&gt; obj  
  
func 함수를 화살표 함수로 선언하면?  
func 함수의 this는 window이고 고로 this는 window로 바뀐다.

### 이벤트 callback 함수의 this

```javascript
const btn = document.querySelector('#btn');
btn.addEventListener('click', function() {
  console.log(this); //button
});

btn.addEventListener('click', () => {
  console.log(this); //window
});

```

function 콜백함수 내의 this는 button을 가리키지만, 화살표 함수의 this는 상위컨텍스트 window를 가리킨다.

### **화살표 함수 arguments**

```javascript
function func (x){
 console.log(arguments);
}

const arrow = (x)=>{
	console.log(arguments); //x
}

func();
arrow();
```

function 키워드로 선언한 함수는 내부적으로 arguments 객체를 갖고 있지만, 화살표 함수는 없다.

```javascript
function func(x) {
  if (arguments.length === 2) {
    console.log('파라미터 두개들어왔다!');
  }
}


func(1,2);
```

이런식으로 파라미터 갯수에 따라 다른 행동을 할 수있지만, 화살표함수는 불가능하다.

```javascript
const func = (...x) => {
  if (x.length === 2) {
    console.log('파라미터 두개 들어왔다!!');
  }
}


func(1, 2);

```

화살표 함수로 똑같이 구현한다면  Spread 문법으로 구현 할 수 있다.

### call, apply, bind

명시적으로 this를 바인딩 해주는 함수이다.

```javascript
function func(a,b) {
  this.a = a;
  this.b = b;
}

const obj = {
  lang: 'javascript'
}

func.call(obj,1,2); // func함수 호출시 this를 obj로 바인딩 후 호출
console.log(obj); //{lang,a,b}
```

하지만 화살표 함수는 this를 변경 할 수 없다.

```javascript
const func = (a, b) => {
  this.a = a;
  this.b = b;
}

const obj = {
  lang: 'javascript'
}

func.call(obj, 1, 2);
console.log(obj); //{lang}

```

