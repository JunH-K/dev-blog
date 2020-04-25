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

* reduce
* some
* every

