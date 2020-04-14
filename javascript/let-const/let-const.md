# let, const

> 변수 선언 키워드 let, const

es6 이전 자바스크립트에서는 var 라는 키워드로 변수 선언을 했었다.  
es6이후 let, const가 추가 되었다. var의 약점을 보완한 변수선언 키워드로 es6 이후 버전으로 코딩한다면 var를 쓸 이유가 전혀없다. 그 이유와 var와의 차이점, 추가기능을 알아본다.

> var 와의 차이점

* **전역에 등록되지 않는다.**

브라우저 기준 최상위 글로벌변수 window가 있다. var 로 선언한 변수는 window의 프로퍼티로 등록이 된다.

```javascript
var a = 1;
console.log(window.a) //1
```

let, const  변수는 등록안된다.

```javascript
let a = 1;
const b = 1;
console.log(window.a); //undefined
console.log(window.b); //undefined
```



* **스코프의 범위**

```javascript
  if (true) {
    var a = 1;
  }

  console.log(a);
```

var 선언 변수는 if 블록 밖에서 a 접근이 가능하다.. 블록의 의미가 없다. 스코프의 범위가 function이다.

```javascript
  if (true) {
    let a = 1;
  }

  console.log(a); //a not is defined
```

var- &gt; let, const 바꾸면 블록 스코프로 전환!! 그래.. 이게 맞지..

* **선언 및 할당**

```javascript
var a = 1;
var a = 2;
var a = 3;

if(true){
 var a = 4;
}

function func(){
 var a = 5;
}

if(true){
 var a = 6;
}

console.log(a);//?? 무엇일까 ??
```

무한정 중복선언이 가능하 결국 마지막 선언 및 할당이 이전값 들을 덮어쓴다.

```javascript
let a = 1;
let a = 1; //x
const b = 2;
const b = 2; //x
```

예상 했겠지만 중복 선언안된다.

* **let과 const 차이**

```javascript
let a = 1;
a = 5; //o

const b = 1;
b = 5 //x
```

let은 재할당되고, const는 재할당 안된다. 끝.

주의 할점은 객체참조는 못바꾸지만 객체안의 프로퍼티 변경은 가능하다.

```javascript
const obj = {a:1};
obj = {b:1} //x
obj.a = 5; //o
```

es6 이상을 사용한다면 const로 거의 대체가 가능하고 변경 할 변수라면 let 쓰면 되겠다.



