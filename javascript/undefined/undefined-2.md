# 배열메소드

## 자바스크립트 배열 메소드 

자바스크립트에서 유용한 배열 메소드를 알아보자. 이 메소드들은 Array.prototype에 정의 되어 있다. 

{% hint style="info" %}
원본배열을 수정하면 \(O\) 수정하지 않으면\(X\) 표기 
{% endhint %}

### Array.prototype.map \(X\)

원본배열을 바꾸지않고 원본배열과 같은 길이의 새로운 배열을 반환한다. 주로 배열 길이만큼 순회 하거나 원본배열에 새로운데이터를 추가할때 사용한다.

```javascript
const arr = [1, 2, 3, 4, 5];

const result = arr.map((value, index) => {
  return value + 'map'; 
});

console.log(result);
//  ["1map", "2map", "3map", "4map", "5map"]
```

### Array.prototype.filter \(X\)

원본배열을 바꾸지 않고 이름그대로 배열의 값들을 필터할 수 있는 메소드이다. 순차적으로 배열을 순회하는데 콜백함수가 return 하는 값이 true 일 경우인 값들만 반환한다.말이 장황한데 \[1,2,3\]인 배열중 원하는 값만 리턴하고 싶을때 쓰인다. 

```javascript
const arr = [1, 2, 3];

const result = arr.filter((value) => {
  return value === 3;
});

console.log(result); // [3]
```

객체배열인 경우

```javascript
const arr = [{
  name: 'A'
}, {
  name: 'B'
}, {
  name: 'C'
}];

const result = arr.filter((value) => {
  return value.name === 'A';
});

console.log(result); // {name:'A'}

```

### Array.prototype.reduce \(X\)

단어 뜻 그대로 배열을 줄여가며 값을 추출할때 이용할 수 있다.

```javascript
const arr = [{
  name: 'A'
}, {
  name: 'B'
}, {
  name: 'C'
}];

const result = arr.reduce((preValue, curValue, index) => {
  return preValue + curValue.name;
}, ''); //초기값

console.log(result); //ABC
```

reduce   
첫번째 파라미터는 콜백함수  
두번째 파라미터는 preValue 초기값이다.  
콜백함수 return 값이 preValue 다음 값으로 할당된다.  
  
위의 실행 순서를 설명하면  
1. '' + 'A'   -&gt; return 'A'  
2. 'A' + 'B' -&gt; return 'AB'  
3. 'AB'+'B' -&gt; return 'ABC'

### Array.prototype.some \(X\)

단어에서 풍기는 느낌대로 콜백 함수내의 조건들이 배열의 요소 중 한가지 경우라도 만족하는지 판단하고 boolean으로 반환한다.  
예를 들어 임의의 숫자배열이 있고 음수가 하나라도 존재하는지 확인하고 싶다면 아래예제로 간단히 확인가능하다.

```javascript
const arr = [7, 4, 8, 4, 3, -1];

const result = arr.some((value) => {
  return value < 0; //배열 요소 중 하나라도 0 이하인가?
});

console.log(result); //true

```

### Array.prototype.every \(X\)

위와 비슷한 함수이며 단지 배열의 요소들이 조건에 모두 만족하는지 판단한다.  
배열의 임의의 숫자들이 모두 양수인지 확인하는 예제

```javascript
const arr = [7, 4, 8, 4, 3, -1];

const result = arr.every((value) => {
  return value > 0; //배열의 모든 요소가 0 이상인가?
});

console.log(result); //false

```

### Array.isArray\(배\)

배열인지 판별하는 메소드

```javascript
console.log(Array.isArray([])); //true
console.log(Array.isArray([1])); //true
console.log(Array.isArray(new Array(1,2,3))); //true

```

### Array.prototype.flat \(X\)

배열의 중첩배열을 펼치는? 메소드이다. flat 인자는 펼치는 깊이를 입력한다.

```javascript
const arr = [1,2,[3,4,[5,6]]];
console.log(arr.flat()); //[1, 2, 3, 4, [5, 6]]
console.log(arr.flat(1)); //[1, 2, 3, 4, [5, 6]]

console.log(arr.flat(2)); //[1, 2, 3, 4, 5, 6]
console.log(arr.flat(Infinity)); //[1, 2, 3, 4, 5, 6]
```

### Array.from \(X\)

유사배열이나 이터러블객체를 복사해 배열을 만든다.

```javascript
function func() {
  console.log(arguments[0]); //1 index 접근
  console.log(Array.isArray(arguments)); //false

  /*   arguments.map((value) => { //없는 map 메서드
      return value;
    }); 
    */

  Array.from(arguments).map((value) => { //배열로 변환 후 map 사용가능
    console.log(value); //1,2,3
  });

}

func(1, 2, 3);

```

### Array.prototype.fill \(O\)

정적인 값 하나를 배열 요소 값으로 채운다. 배열을 임의로 만들고 값을 채울때 쓰면된다..

```javascript
const arr = new Array(100);
console.log(arr); //[undefined...] 100개
arr.fill(1);
console.log(arr); //[1...] 100개
```

### Array.prototype.sort \(O\)

배열의 요소를 정렬한다.

```javascript
const arr = [3,1,2,5,2];
console.log(arr.sort()); //[1, 2, 2, 3, 5]
console.log(arr); //[1, 2, 2, 3, 5]
```

기본적으로 오름차순 정렬한다. 

sort 인자로 비교 함수를 정의할 수 있다.

```javascript
const arr = [3, 1, 2, 5, 2];

function asc(a, b) {
  return a - b;
}

function desc(a, b) {
  return b - a;
}

console.log(arr.sort(asc)); //[1, 2, 2, 3, 5]
console.log(arr.sort(desc)); //[5, 3, 2, 2, 1]

```

비교함수 반환값이 

음수이면 a가 b 앞에  
양수이면 a가 b 뒤로  
0이면 그대로 

규칙으로 정렬한다.

