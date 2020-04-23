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



> 자바스크립트 빈 객체인지 확인하기

자바스크립트에서 빈 객체인지 확인이 필요할 때가 있다. undefined나 null이면 " ! " 연산자로 바로 확인이 가능하지만 객체는 프로퍼티가 있건 없건 논리적 true로 간주하기 때문에 다른 방법으로 확인해야한다. 







