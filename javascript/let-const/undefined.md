# 화살표 함수

function 키워드 대신 화살표로 간략한 함수 표현이 가능하다. 익명함수로만 사용가능하 함수표현식으로 사용한다.



> 다양한 선언 방식

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

> function 키워드 선언과의 차이점

