# 구조분해할당

배열이나 객체를 분해하여 변수에 할당하는 문법이다.

> 배열 구조 분해 할당

```javascript
const [a, b] = [1,2,3] //1번
console.log(a); //1
console.log(b); //2

const [c,...rest] = [1,2,3] //2번
console.log(c); //1
console.log(rest); //[2,3]

const [d, ,f] = [1,2,3] //3
console.log(d); //1
console.log(f); //3

let g = 10;
let h = 20;
[g, h] = [h, g];//4
console.log(g); //20
console.log(h); //10
```

1. 순서대로 a, b에 값을 할당하고 3은 무시한다.
2. 순서대로 c에 1을 할당하고 spread문법으로 나머지를 rest에 할당한다.
3. 두번째자리를 비움으로써 d, f 순서대로 1, 3을 할당한다.
4. 두 값을 바꿀수도 있다.

> 객체 분해 구조할당

```javascript
const {a, b} = {a: 1, b: 2}; //1번
console.log(a); //1
console.log(b); //2

const {a = 1, b} = {b: 2}; //2번
console.log(a); //1
console.log(b); //2

const {a:aa, b:bb} = {a: 1, b: 2}; //3번
console.log(aa); //1
console.log(bb); //2

const {a:aa = 1, b:bb} = {b: 2}; //4번 
console.log(aa); //1
console.log(bb); //2
```

1. 우측 객체 프로퍼티를 좌측 변수에 대입한다. 좌측 변수이름은 가져올 객체 프로퍼티와 같아야 한다.
2. 위와 같지만 값을 가져올 객체에  a 프로퍼티가 없거나 값이 undefined이면 a 기본값을 1로 할당한다.
3. 1과 같지만 변수이름을 aa 와 bb 로 변경한다.  a는 변수로써 못쓰이고 aa로만 쓸 수 있다.
4. 1,2,3의 조합 - 객체 프로퍼티를 a, b로 변수로 할당하지만 이름은 aa, bb로 변경하고, a프로퍼티가 없거나 값이 undefined 이면 aa 기본값을 1로 할당한다. 

