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





