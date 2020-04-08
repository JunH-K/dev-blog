# React.js

## React 16.8에 새로 추가된 Hook 종류와 개념

[![HitCount](http://hits.dwyl.com/JunH-K/https://githubcom/JunH-K/react-gitbook.svg)](http://hits.dwyl.com/JunH-K/https://githubcom/JunH-K/react-gitbook)

작성중..

> Hook

함수형 컴포넌트에서도 클래스형 컴포넌트의 기능을 사용할 수 있게 하는 기능이다.  
훅을 통해 함수형 컴포넌트에서도 컴포넌트 상탯값을 관리할 수 있고, 컴포넌트의 생명 주기 함수를 이용할 수 있다.



> 장점

재사용 가능한 로직을 쉽게 만든다. 훅이 단순한 함수이므로 함수 안에서 다른 함수를 호출하는 것으로 새로운 훅을 만들 수 있기 때문이다. 리액트 내장 훅과 다른 사람들이 만든 여러 커스텀 훅을 조립해서 쉽게 새로운 훅을 만들 수 있다.  
같은 로직을 한곳으로 모을 수 있어 가독성이 좋다.



> 기본 Hook

* [useState](hook/usestate.md)
* [useEffect](hook/useeffect.md)
* useContext

> 추가 Hook

* useReducer
* useCallback
* useMemo
* useRef
* useImperativeHandle
* useLayoutEffect
* useDebugValue

> Custom hook

