# 호이스팅

> 자바스크립트 호이스팅

호이스팅은 변수와 함수 호이스팅이 있다. 말 그대로 선언이전에 끌여올려진다는 의미이다. 

변수와 함수는 여러 선언 방법이 있는데 각각 차이점이 존재하여 그 차이점을 알아본다.

> var

```javascript
console.log(js); //undefined
var js = 'javascript';
```

var js 선언 이전에 변수 참조가 가능하다. 실제 할당문이 도달전에 이미 js 변수가 선언되고 undefined로 초기화가 되어있다. 문맥 구조상 선언되지 않은 변수를 쓰는것도 가독성면에서 좋지도 않고 이전에 참조할 수 있게 시스템에서 초기화 해준것도 좋지 않은것같다. 이제는 쓰지말자..

> let, const

```javascript
console.log(js); //ReferenceError
console.log(java); 
let js = 'javascript';
const java = 'java';
```

var 의 단점을 모두 보완하며 선언전에 참조하면 참조에러가 발생한다. 그렇다고 호이스팅이 되지 않은것이 아니라 초기화가 진행되지 않아서 참조에러가 발생한 것이다.

```javascript
let js = 'javascript';

if (1) {
  console.log(js); //1. ReferenceError
  let js = 'js';
}
```

하위 스코프에서 상위스코프 변수는 당연히 참조 가능하고 if블록 1번에서 js 접근하면 'javascript'가 나와야 될거 같지만 블록내에 js 선언이 끌어 올려지면서 referenceError가 발생한다.

> 함수선언식

```text

```

> 함수표현

```text

```

