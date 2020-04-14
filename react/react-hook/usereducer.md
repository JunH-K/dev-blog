# useReducer

> 컴포넌트의 상태값을 리덕스의 리듀서 처럼 관리하기



```javascript

const INITIAL_STATE = { name: '' }; // 초기 상태값

const reducer = (state, action) => {
  switch (action.type) {
    case 'setName':
      return {
        ...state,
        name: action.name,
      };
  }
};

function App() {
  const [state, dispatch] = useReducer(reducer, INITIAL_STATE);
  const onChange = (e) => {
    dispatch({ type: 'setName', name: e.target.value });
  };

  return (
    <div className="App">
      <input type="text" value={state.name} onChange={onChange} />
    </div>
  );
}

```

> 데이터 흐름

onChange -&gt; dispatch -&gt; action -&gt; reducer \(setName\) -&gt; update state -&gt; 랜더

