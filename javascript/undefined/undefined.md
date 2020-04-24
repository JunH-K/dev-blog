# 데이터타입

자바스크립트 데이터 타입

* 원시타입
  * number
    * Infinity
    * NaN
  * string
  * null
  * undefined
  * boolean
  * symbol
* 객체타입
  * object



데이터타입은 원시타입 6개 객체타입1개가 있다.

* number

다른언어와 달리 float double건 없고 number 타입으로 모든숫자를 표현한다.

```javascript
const num = 1;
const num2 = 1.1;
const num3 = -1.1;
const infi = 1 / 0; //무한대
const nan = 1 * {}; // Not a number 산술 연산 불가

console.log(typeof num);
console.log(typeof num2);
console.log(typeof num3);
console.log(typeof infi);
console.log(typeof nan);
```

typeof로 검사하면 위 모든값은 "number" 이다.



* 문자열

```javascript
const str = "쌍따옴표 문자열";
const str2 = '따옴표 문자열';
const str3 = `템플릿 리터럴 es6에 생김`;
```

세 가지 방식으로 표현 가능하다. 아무거나 선택해서 써도 되지만 일관성을 맞추기위해서 개인적으로 [prettier](https://www.npmjs.com/package/prettier)를 쓴다. "", '' 중 옵션으로 선택하면 파일저장할때 선택한 옵션으로 자동으로 다 바꿔준다. 편리..

 \` 백틱\(키보드 숫자 1 왼쪽\)으로 표현하는 문자열은 es6에서 생겼고, 써본결과 문자열을 합칠때 깔끔하게 표현이 가능한거 같다.

```javascript
const java = '자바';
const script = '스크립트';

console.log(java + script + ' 공부합시다.');
console.log(`${java}${script} 공부합시다.`);

```

```javascript
const script = '스크립트';
const str = '';
const num = '1';

console.log(typeof script); //string
console.log(typeof str); //string
console.log(typeof num); //string

```

* null

특별한 타입이며 null은 null값만 가질수 있다. 값이 없다는걸 명시적으로 표현할때 쓰인다. undefined와 같이 뭔가 없다는걸 표현하는것이 비슷하지만 undefined는 선언하고 값을 할당하지 않을때 시스템에서 자동으로 초기화해주는 값이다. 따라서 개발자가 명시적으로 값이 없다라는걸 표현할 때에만 null을 쓰는것이 일관성 있게 쓰일 수 있을 것같다.

```javascript
let obj;
const func = (param) => {
  console.log(param); //undefined
}
func();
console.log(obj);//undefined
```

주의할 점은 typeof 검사시 object 이다. 찾아보면 설계상의 오류라고한다. 만약 조건문으로 쓰인다면 다음과 같이 한다.

```javascript
const obj = null;

console.log(typeof obj === 'object'); //true

if (obj === null) {
  console.log('null이다');
}
```

* undefined

```javascript
let a;
const obj = {};
const func = (param) => {
  console.log(param); // undefined
}

func();
console.log(a); //undefined
console.log(obj.a); //undefined

```

특별한 타입이며 undefined는 undefined만 가질 수 있다. 변수를 선언하거나 객체에 없는 프로퍼티에 접근했을때 자바스크립트 엔진이 명시적으로 undefined를 할당한다. 고로 개발자가 선언을 했지만 값을 초기화 안한 변수라고 알 수 있다. 의도적으로 값을 할당하지 않는것을 표현 할땐 null을 할당한다. 그래야 의도적인지 아닌지 판단할 수 있다.



* boolean

논리적 참과 거짓을 나타낸다. 주로 조건문에 쓰이며, 변수명은 대체로 isXXXX로 명명한다.  
각 데이터 값 앞에 \(!\) 느낌표 논리NOT 연자를 써서 boolean 데이터타입으로 변환할 수 있다.  
''\(빈문자열\), 0, undefined, null -&gt; true가 되고 나머지는 모두 false이다.  


```javascript
const isComplete = true;
console.log(!''); //true
console.log(!0); //true
console.log(!undefined); //true
console.log(!null); //true

console.log(!1); //false
console.log(!'JS'); //false
console.log(!{}); //false
console.log(![]); //false
console.log(!function func(){}); //false
```





* symbol

새로추가된 원시타입 값이며 Symbol\(\) 로 생성한 값은 유일한 값이라고 한다. 이 값은 객체 프로퍼티로 사용되며 유일한 목적이라고 한다. 

```javascript
const s1 = Symbol();
const s2 = Symbol();
console.log(s1 === s2); //false

const a1 = Symbol('a');
const a2 = Symbol('a');
console.log(a1 === a2); //false

const obj = {};
obj[s1] = 1;
console.log(obj[s1]); //1


```

* object 객체타입

원시타입을 제외한 모든것이 객체이다

```javascript
const obj = {
  name: 'JS',
  getName() {
    return this.name;
  }
}

const arr = [1, 2, 3]
const func = () => {
  return obj;
}
```

