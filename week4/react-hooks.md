# 3.React의 Hook

## React Hook 이란

React Hooks는 React 버전 16.8에 도입된 기능으로, 이전에는 class component에서만 사용할 수 있었던 functional component에서 개발자가 상태 및 기타 React 기능을 사용할 수 있도록 한다.
Hooks는 React 코드를 작성하는 더 간단하고 간결한 방법을 제공하고 component 간에 코드를 더 쉽게 재사용하고 공유할 수 있도록 한다.

## Hooks

### useState

component가 functional component의 상태를 관리할 수 있도록 하는 가장 일반적으로 사용되는 hook이다.
초기 상태 값을 받아 현재 상태 값과 상태 값을 업데이트하는 함수의 두 가지 요소가 포함된 배열을 반환한다.
상태 값이 변경될 때마다 component는 새 상태 값으로 다시 렌더링된다.

```js
const [count, setCount] = useState(0);

return (
  <div>
    <p>You clicked {count} times</p>
    <button onClick={() => setCount(count + 1)}>Click me</button>
  </div>
);
```

### useEffect

useEffect를 사용하면 component가 API에서 데이터를 가져오거나 DOM을 업데이트하는 것과 같은 side effect를 functional component에서 수행할 수 있다.
side effect를 수행하는 함수를 사용하고 component를 렌더링할 때마다 실행한다.
개발자는 component가 마운트 해제된 후 또는 다음 효과가 실행되기 전에 실행할 정리 기능을 지정할 수도 있다.

```js
useEffect(() => {
  document.title = `You clicked ${count} times`;
}, [count]);
```

### useContext

useContext를 사용하면 component가 상위 component에서 제공하는 컨텍스트 값을 사용할 수 있다.
컨텍스트 개체를 사용하고 현재 컨텍스트 값을 반환한다.
컨텍스트 값이 변경되면 component가 새 값으로 다시 렌더링된다.

```js
import React from 'react';

const UserContext = React.createContext();

export default UserContext;
```

```js
import React from 'react';
import UserContext from './UserContext';

export default function App() {
  const user = { name: 'John Doe', email: 'johndoe@example.com' };

  return (
    <UserContext.Provider value={user}>
      <Greeting />
    </UserContext.Provider>
  );
}
```

```js
import React, { useContext } from 'react';
import UserContext from './UserContext';

const user = useContext(UserContext);

export default function Greeting() {
  const user = useContext(UserContext);

  return (
    <div>
      Hello, {user.name}!
    </div>
  );
}
```

### useRef

useRef를 사용하면 component가 다시 렌더링하는 동안 지속되는 값에 대한 변경 가능한 참조를 만들 수 있다.
DOM 요소 또는 여러 렌더링에서 액세스해야 하는 다른 값에 할당할 수 있는 변경 가능한 ref 개체를 반환한다.

```js
const inputRef = useRef(null);

return (
  <div>
    <input ref={inputRef} />
    <button onClick={() => inputRef.current.focus()}>Focus input</button>
  </div>
);
```

### useLayoutEffect

useLayoutEffect는 useEffect()와 유사하지만 모든 DOM 변형이 완료된 후 브라우저가 업데이트된 화면을 그리기 전에 동기적으로 실행된다.
DOM 요소를 측정하거나 업데이트된 DOM의 정확한 측정이 필요한 기타 작업을 수행하는 데 유용한다.

```js
useLayoutEffect(() => {
  const dimensions = inputRef.current.getBoundingClientRect();
  console.log(dimensions);
}, [inputRef.current]);

return (
  <div>
    <input ref={inputRef} />
  </div>
);
```

## React StrictMode 란

React의 StrictMode는 개발 중에 React 애플리케이션의 잠재적인 문제를 강조 표시하는 개발자 도구다.
StrictMode가 활성화되면 React는 추가 검사를 수행하고 일반적인 실수와 잠재적인 버그를 식별하는 데 도움이 되는 경고를 내보낸다.

1. 예기치 않은 동작을 유발할 수 있는 componentWillMount 및 componentWillReceiveProps와 같은 안전하지 않은 수명 주기 메서드를 식별한다.
2. 불필요한 재렌더링을 유발할 수 있는 상태 설정과 같은 렌더링 방법의 잠재적인 부작용을 강조 표시한다.
3. component에서 발생하는 처리되지 않은 오류 감지.

StrictMode는 프로덕션 모드에서 애플리케이션의 동작에 영향을 주지 않으며 개발 중에만 사용된다.
StrictMode를 활성화하려면 앱 또는 특정 component를 `<React.StrictMode>` component로 래핑하기만 하면 된다.

`v18이전`

```js
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```

`v18이후`

```js
import React from 'react';
import { createRoot } from 'react-dom/client';

const container = document.getElementById('root');

if (!container) {
  return;
}

const root = createRoot(container);

root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
);
```

## Reference

- [React Today and Tomorrow and 90% Cleaner React With Hooks](https://www.youtube.com/watch?v=dpw9EHDh2bM)
- [useEffect 완벽 가이드](https://overreacted.io/ko/a-complete-guide-to-useeffect/#%ED%95%A8%EC%88%98%EB%A5%BC-%EC%9D%B4%ED%8E%99%ED%8A%B8-%EC%95%88%EC%9C%BC%EB%A1%9C-%EC%98%AE%EA%B8%B0%EA%B8%B0)
