# 4.usestore-ts

## usesotre-ts

- React 상태 관리 라이브러리

```ts
import { Store, Action, useStore } from 'usestore-ts';

@Store()
class CounterStore {
  count = 0;

  @Action()
  increase() {
    this.count += 1;
  }

  @Action()
  reset() {
    this.count = 0;
  }
}

const counterStore = new CounterStore();

export default function Counter() {
  const [{ count }, store] = useStore(counterStore);

  return (
    <div>
      <p>
        Count:
        {' '}
        {count}
      </p>
      <p>
        <button type="button" onClick={() => store.increase()}>
          Increase
        </button>
        <button type="button" onClick={() => store.reset()}>
          Reset
        </button>
      </p>
    </div>
  )
}
```

- 상태를 관리하는 스토어 클래스의 필수로 가지고 있어야 하는 내부 메소드를 usestore-ts의 어노테이션을 통해서 손쉽게 사용이 가능하다.

## [useSyncExternalStore](https://react.dev/reference/react/useSyncExternalStore#usesyncexternalstore)

useSyncExternalStore외부 저장소를 구독할 수 있는 React Hook입니다.
`useSyncExternalStore(subscribe, getSnapshot, getServerSnapshot?)`

```js
import { useSyncExternalStore } from 'react';
import { todosStore } from './todoStore.js';

function TodosApp() {
  const todos = useSyncExternalStore(todosStore.subscribe, todosStore.getSnapshot);
  // ...
}
```

저장소에 있는 데이터의 스냅샷을 반환합니다. 두 함수를 인수로 전달해야 합니다.

1. 함수 subscribe는 스토어를 구독하고 구독을 취소하는 함수를 반환해야 합니다.
2. 함수 getSnapshot는 저장소에서 데이터의 스냅샷을 읽어야 합니다.

### 매개변수

- subscribe: 단일 콜백 인수를 받아 스토어에 구독하는 함수입니다.
스토어가 변경되면 제공된 콜백을 호출해야 합니다.
그러면 컴포넌트가 다시 렌더링됩니다.
 구독 함수는 구독을 정리하는 함수를 반환해야 합니다.
- getSnapshot: 컴포넌트에 필요한 스토어 데이터의 스냅샷을 반환하는 함수입니다.
저장소가 변경되지 않은 상태에서 getSnapshot을 반복적으로 호출하면 동일한 값을 반환해야 합니다.
저장소가 변경되고 반환된 값이 다른 경우(Object.is에 의해 비교됨), React는 컴포넌트를 다시 렌더링합니다.

- getServerSnapshot(optional): 스토어에 있는 데이터의 초기 스냅샷을 반환하는 함수입니다.
서버 렌더링 중과 클라이언트에서 서버 렌더링 콘텐츠의 하이드레이션 중에만 사용됩니다.
서버 스냅샷은 클라이언트와 서버 간에 동일해야 하며, 일반적으로 직렬화되어 서버에서 클라이언트로 전달됩니다.
이 인수를 생략하면 서버에서 컴포넌트를 렌더링할 때 오류가 발생합니다.

### Returns

- 렌더링 로직에 사용할 수 있는 스토어의 현재 스냅샷입니다.

### 주의 사항

- getSnapshot이 반환하는 스토어 스냅샷은 변경 불가능해야 합니다.
기본 스토어에 변경 가능한 데이터가 있는 경우 데이터가 변경된 경우 변경 불가능한 새 스냅샷을 반환합니다.
그렇지 않으면 캐시된 마지막 스냅샷을 반환합니다.

- 다시 렌더링하는 동안 다른 구독 함수가 전달되면 React는 새로 전달된 구독 함수를 사용하여 스토어를 다시 구독합니다.
컴포넌트 외부에서 구독을 선언하면 이를 방지할 수 있습니다.
