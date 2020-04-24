# 타입 및 객체 체크

> 자바스크립트에서  타입 체크하기

* number 

```javascript
const num = 1.1;
const num2 = NaN;
const num3 = Infinity;

console.log(typeof num);
console.log(typeof num2);
console.log(typeof num3);
```

3가지 모두 number 타입이며 특히 NaN과 Infinity도 number 타입이기때문에 실제 정수를 확인하려면 isNaN\(\)등으로 한번더 확인해야한다.



* string

```javascript
const str1 = '';
const str2 = '1';
const str3 = 'str';

console.log(typeof str1 === 'string'); 
console.log(typeof str2 === 'string');
console.log(str3.constructor === String);
```

문자열 타입체크

* undefined

```javascript
let a;
console.log(a === undefined); //true
console.log(typeof undefined === 'undefined'); //true

if(!a){
 console.log('a는 undefined');
}
```

변수선언 후 값을 할당하지 않을때 자동으로 undefined를 할당한다.   
undefined 자체로 확인가능하고 typeof 사용시 문자열로 확인한다.  ! 연산자로 boolean으로 변환 후 사용해도 된다. 주의할 점은 a가 null,  0, ''\(빈문자열\) 이어도 조건문을 통과한다. 

```javascript
let a = 0;


if(!a){
 console.log('a는 undefined, null, 0, '' 중 하나!');
}
```

* null

```javascript
let a = null;

console.log(a === null);
console.log(typeof null === 'object'); // true

if(!a){
console.log('a는 undefined, null, 0, '' 중 하나!');
}
```

사용자가 명시적으로 null을 할당하고 어디선가 확인할때 null  검사할 수 있다. typeof 는 object가 나오기때문에 사용할 수 없다. 

> 자바스크립트 빈 객체인지 확인하기

자바스크립트에서 빈 객체인지 확인이 필요할 때가 있다. undefined나 null이면 " ! " 연산자로 바로 확인이 가능하지만 객체는 프로퍼티가 있건 없건 논리적 true로 간주하기 때문에 다른 방법으로 확인해야한다. 

```javascript
const obj = {}

if(obj){
	console.log('객체있다~');
}
```

위와 같이 객체가 비어있어도 true로 간주된다. 따라서 프로퍼티 존재확인을 위해서는 다른방법을 써야한다.

```javascript
const obj = {};

function hasProp(obj, prop) {
  return !!obj[prop];
}

console.log(hasProp(obj, 'a'));
```

해당객체에 prop으로 가져오고 !! 로 boolean으로 변환한다. 느낌적으론 될것같지만 만약a의 값이0이나 undefined,null 이면 예상했던 결과가 나오지않는다. 이건 패스..



