# 배열메소드

자바스크립트에서 유용한 배열 메소드를 알아보자.

* map

원본배열을 바꾸지않고 원본배열과 같은 길이의 새로운 배열을 반환한다. 주로 배열 길이만큼 순회 하거나 원본배열에 새로운데이터를 추가할때 사용한다.

```javascript
const arr = [1, 2, 3, 4, 5];

const result = arr.map((value, index) => {
  return value + 'map'; 
});

console.log(result);
//  ["1map", "2map", "3map", "4map", "5map"]
```

* filter

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

* reduce

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

* some

단어에서 풍기는 느낌대로 콜백 함수내의 조건들이 배열의 요소 중 한가지 경우라도 만족하는지 판단하고 boolean으로 반환한다.  
예를 들어 임의의 숫자배열이 있고 음수가 하나라도 존재하는지 확인하고 싶다면 아래예제로 간단히 확인가능하다.

```javascript
const arr = [7, 4, 8, 4, 3, -1];

const result = arr.some((value) => {
  return value < 0; //배열 요소 중 하나라도 0 이하인가?
});

console.log(result); //true

```



* every

위와 비슷한 함수이며 단지 배열의 요소들이 조건에 모두 만족하는지 판단한다.  
배열의 임의의 숫자들이 모두 양수인지 확인하는 예제

```javascript
const arr = [7, 4, 8, 4, 3, -1];

const result = arr.every((value) => {
  return value > 0; //배열의 모든 요소가 0 이상인가?
});

console.log(result); //false

```

