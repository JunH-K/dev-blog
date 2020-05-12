# 제너레이터

제너레이터 함수는 이터러블을 생성하는 함수이다. 일반 함수와 달리 한번에 코드블록을 실행하지 않고 함수 코드블록을 실행 중지 했다가 필요한 시점에 재시작 할 수 있는 함수이다.

```javascript
function* counter() {
  let count = 1;
  console.log('첫 번째');
  yield count++;
  console.log('두 번째');
  yield count++;
  console.log('세 번째');
  yield count++;
}

const gene = counter();
console.log(gene.next());
console.log(gene.next());
console.log(gene.next());

```

제너레이터 함수를 호출하면 제너레이터를 반환한다. 이 제너레이터는 이터러블이면서 이터레이터이다.

이터러블 : symbol.iterator 메소드를 소유한 객체  
이터레이터 : next 메소드를 소유하며 이 메소드를 호출하면{ value, done } 프로퍼티를 갖는 객체를 반환한다. 

고로 제너레이터는 for..of문으로 순회가 가능하다.

```javascript
function* counter() {
  let count = 1;
  console.log('첫 번째');
  yield count++;
  console.log('두 번째');
  yield count++;
  console.log('세 번째');
  yield count++;
}


for (let value of counter()) {
  console.log(value);
}
```



