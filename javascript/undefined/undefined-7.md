# 함수

함수는 어떤작업을 하나의 단위로 실행되는 코드집합 문 이다.  함수는 이름과 매개변수가 있고 필요할 때에 호출되어 집합코드 블럭을 실행 할 수 있다.

* print 라는 함수 선언

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

