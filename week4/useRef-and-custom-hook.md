# 4.useRef & Custom Hook

## useRef

## Hook의 규칙

React의 Custom Hooks는 구성 요소에서 재사용 가능한 논리를 추출하고 여러 구성 요소 간에 공유할 수 있는 기능이다.
다음은 사용자 지정 후크를 만들 때 염두에 두어야 할 몇 가지 일반적인 규칙이다.

1. 함수 이름을 'use'로 시작해야 한다. 규칙에 따라 React의 모든 사용자 지정 후크는 'use'라는 단어로 시작해야 한다. 이렇게 하면 다른 개발자가 해당 함수가 후크로 사용된다는 것을 알 수 있기 때문이다.

2. 사용자 정의 후크 내에서 다른 후크 사용: 사용자 정의 후크는 구성 가능하도록 되어 있으므로 사용자 정의 후크 내에서 useState, useEffect 및 useContext와 같은 다른 후크를 자유롭게 사용해야 한다.

3. 사용자 지정 후크의 최상위 수준에서만 후크 호출: 후크는 내부 루프, 조건 또는 중첩 함수가 아닌 구성 요소 또는 사용자 지정 후크의 최상위 수준에서만 호출해야 한다. 즉, 여러 번 호출될 수 있는 콜백 또는 이벤트 핸들러 내에서 후크를 호출해서는 안 된다.

4. 배열 또는 개체 반환: 사용자 지정 후크는 항상 배열 또는 개체를 반환해야 한다. 이렇게 하면 후크를 사용하는 구성 요소에서 값을 쉽게 분해하고 사용할 수 있기 때문이다.

5. 사용자 지정 후크 문서화: 코드의 다른 함수나 구성 요소와 마찬가지로 사용자 지정 후크를 명확한 주석으로 문서화하고 기능, 사용 방법, 매개 변수 또는 반환 값을 설명하는 것이 중요한다.

6. 사용자 지정 후크 테스트: 사용자 지정 후크를 철저히 테스트하여 예상대로 작동하고 극단적인 경우나 예기치 않은 입력을 처리하는지 확인하십시오.

`usehooks-ts`의 `useBoolean` 커스텀 훅

```ts
import { Dispatch, SetStateAction, useCallback, useState } from 'react'

interface UseBooleanOutput {
  value: boolean
  setValue: Dispatch<SetStateAction<boolean>>
  setTrue: () => void
  setFalse: () => void
  toggle: () => void
}

function useBoolean(defaultValue?: boolean): UseBooleanOutput {
  const [value, setValue] = useState(!!defaultValue)

  const setTrue = useCallback(() => setValue(true), [])
  const setFalse = useCallback(() => setValue(false), [])
  const toggle = useCallback(() => setValue(x => !x), [])

  return { value, setValue, setTrue, setFalse, toggle }
}

export default useBoolean
```

`사용`

```ts
import { useBoolean } from 'usehooks-ts'

export default function Component() {
  const { value, setValue, setTrue, setFalse, toggle } = useBoolean(false)

  // Just an example to use "setValue"
  const customToggle = () => setValue((x: boolean) => !x)

  return (
    <>
      <p>
        Value is <code>{value.toString()}</code>
      </p>
      <button onClick={setTrue}>set true</button>
      <button onClick={setFalse}>set false</button>
      <button onClick={toggle}>toggle</button>
      <button onClick={customToggle}>custom toggle</button>
    </>
  )
}
```

## Reference

- [Reusing Logic with Custom Hooks(커스텀 훅으로 로직 재사용)](https://react.dev/learn/reusing-logic-with-custom-hooks)
- [자신만의 Hook 만들기](https://ko.legacy.reactjs.org/docs/hooks-custom.html)
