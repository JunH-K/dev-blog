# 함수

함수는 어떤작업을 하나의 단위로 실행되는 코드집합 문 이다.  함수는 이름과 매개변수가 있고 필요할 때에 호출되어 집합코드 블럭을 실행 할 수 있다.

> 함수 선언

function 키워드로 이름이 있는 함수를 만드는것이 함수선언식이라 한다.

```javascript
function print(){
    return 'hello';
}

const result = print();
```

* 함수이름 : print
* 함수몸체 : '{' 로 시작 '}'로 끝.
* return : 함수를 실행시 돌려주는 값. 기본값은 undefined 
* result : print\(\);구문으로 함수를 실행하고 'hello'를 돌려받아 result 변수에 할당한다.

> 함수 표현식

이름이 없는 함수를 만들고 변수에 할당하는 것을 함수 표현식이라고 한다. 선언식과 동작이 같지만 선언 이전에는 호출 할 수 없다.

```javascript
const print = function(){
    return 'hello';
}
;
```



> 매개변수

함수에 정보를 전달 할 수 있다.

```javascript
function add(a, b) {
  return a + b;
}

console.log(add(1,2));
console.log(add(1)); // NaN
```

add 함수에 1, 2를 전달하여 1 + 2 를 돌려준다. 전달하는 값이 없으면 기본값으로 undefined가 할당된다.  
매개변수는 함수스코프 규칙에 따라 함수 내부에서만 접근 가능하다.

매개변수로 1 하나 전달시 1 + undefined = NaN 숫자계산이 불가능하여 Not a Number를 돌려준다.



