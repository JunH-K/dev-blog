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
* reduce
* some
* every

