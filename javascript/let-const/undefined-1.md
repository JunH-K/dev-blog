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

