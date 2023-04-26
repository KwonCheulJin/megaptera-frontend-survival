# 2.React State

## React state란?

React에서 state(상태)는 components(구성 요소) 내에서 데이터를 관리하는 방법이다.
구성 요소의 내부 상태를 나타내며 구성 요소 자체에서 수정할 수 있다.
구성 요소의 상태가 변경되면 React는 자동으로 구성 요소와 해당 하위 구성 요소를 다시 렌더링하여 업데이트된 상태를 반영한다.

```js
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(prev => prev + 1)}>Increment</button>
    </div>
  );
}
```

이 예에서 Counter 구성요소는 useState를 사용하여 0으로 초기화된 count라는 상태 변수를 정의한다.
또한 상태 값을 업데이트하기 위해 setCount 함수를 사용한다.

버튼을 클릭하면 익명 함수가 호출되며 setCount 함수를 사용하여 count 상태 값을 업데이트한다.
그런 다음 React는 업데이트된 상태 값으로 구성 요소를 다시 렌더링하여 새 count 값이 표시되도록 한다.

'useState'를 사용하면 클래스 구성 요소나 구성 요소의 'props'를 수동으로 조작할 필요 없이 기능적 구성 요소에서 상태 값을 정의하고 업데이트할 수 있다.

## DRY 원칙

"Don't Repeat Yourself"(DRY)는 코드 반복을 줄이고 기존 코드의 재사용을 최대화하는 것을 옹호하는 소프트웨어 개발 원칙이다.
이 원칙은 지식이나 논리의 모든 부분이 시스템 내에서 단일하고 모호하지 않은 표현을 가져야 한다고 명시한다.

실제로 이것은 코드를 작성할 때 개발자가 동일한 기능이나 논리를 여러 위치에 복제하지 않아야 함을 의미한다.
이는 코드 부풀림, 복잡성 증가 및 잠재적인 버그로 이어질 수 있기 때문이다.
대신 공통 기능은 필요에 따라 코드베이스 전체에서 사용할 수 있는 재사용 가능한 모듈, 함수 또는 클래스로 추상화되어야 한다.

DRY 원칙을 따르면 더 깨끗하고 유지 관리하기 쉬운 코드를 만들 수 있으며 버그가 적고 변경이 더 쉽다.
또한 논리가 중앙 집중화되고 코드베이스 전체에 분산되지 않기 때문에 코드를 더 쉽게 테스트하고 리팩터링할 수 있다.

리액트에서 작업하다보면 자연스럽게 이 원칙을 지키게 되는 것 같다.
UI작업을 하다보면 동일 형태의 UI를 여러 화면에서 보여줘야 하는 경우가 많은데 이럴경우에 화면마다 컴포넌트를 작성하게 된다면 관리해야하는 컴포넌트가 자연스럽게 늘어나는거고 그러다보면 같은 수정을 하더라도
수정 작업을 하던 중에 같은 형태이지만 다른 버그가 발생할 수 도있다.

그래서 작업을 하면서 비슷한 폼을 가지는 UI또는 동일한 기능을 가지는 함수들을 공용으로 따로 작업을 해서 한 곳에서 유지 보수 할 수 있도록 작업하는게 중요하다고 생각된다.

## SSOT(Single Source of Truth)

SSOT(Single Source of Truth)는 시스템의 모든 데이터 조각이 시스템 내에서 모호하지 않은 단일 표현을 가져야 한다고 명시하는 소프트웨어 개발 원칙이다.
즉, 데이터는 필요한 모든 구성 요소에 액세스할 수 있는 중앙 위치에 저장되어야 하며 이 데이터는 해당 특정 정보에 대한 유일한 정보 소스여야 한다.

실제로 이것은 소프트웨어를 개발할 때 개발자가 시스템의 다른 부분에 동일한 데이터의 여러 복사본을 두지 않도록 노력해야 한다는 것을 의미한다.
이는 불일치, 오류 및 리소스 낭비로 이어질 수 있기 때문입니다. 대신 데이터는 해당 데이터의 신뢰할 수 있는 소스 역할을 하는 단일 위치에 저장해야 한다.
애플리케이션의 특정 요구 사항에 따라 데이터베이스, API 또는 파일 시스템이 될 수 있다.

개발자는 SSOT 원칙에 따라 전체 시스템에서 데이터가 일관되고 최신 상태인지 확인하여 버그와 오류를 방지할 수 있다.
또한 변경 사항을 시스템 전체에 복제하는 대신 한 곳에서만 변경하면 되므로 데이터를 보다 쉽게 ​​관리하고 업데이트할 수 있다.

예를 들어 고객 정보를 표시하는 웹 애플리케이션에서 SSOT 원칙은 모든 고객 데이터가 애플리케이션 전반에 걸쳐 여러 위치에 복제되기보다는 단일 데이터베이스에 저장되어야 한다고 제안한다.
이렇게 하면 응용 프로그램의 모든 부분이 동일한 최신 정보로 작동하고 오류나 불일치의 위험이 줄어든다.

## useState

React에서 useState는 기능 구성 요소가 상태를 가질 수 있도록 하는 hook이다.
이전에는 setState를 사용하는 클래스 구성 요소에서만 가능했었는데 요즘은 기능적 구성 요소(Functional components)에서 상태를 정의하고 업데이트하는 방법을 제공한다.

useState hook은 초기 상태 값을 매개변수로 사용하고 현재 상태 값과 해당 상태 값을 업데이트하는 함수의 두 가지 값이 포함된 배열을 반환한다.

```js
const [temporary, setTemporary] = useState();
```

배열의 첫 번째 값은 현재 상태 값으로 구성 요소의 렌더링 메서드에서 액세스하고 표시할 수 있다.
두 번째 값은 상태 값을 업데이트하기 위해 호출할 수 있는 함수로, 구성 요소가 다시 렌더링되도록 한다.

## 1급 객체(first-class object)란?

프로그래밍 언어 설계에서 일급 객체(또는 일급 시민)는 값 또는 객체로 취급되어 매개변수로 전달되거나 함수에서 반환되거나 변수에 할당될 수 있는 엔티티를 설명하는 데 사용되는 용어다.

간단히 말해서 일급 객체는 언어의 다른 값이나 객체처럼 조작할 수 있는 엔티티다.

JavaScript 및 Python과 같은 일부 프로그래밍 언어에서는 함수를 일급 객체로 취급하므로 변수에 할당하거나 다른 함수에 인수로 전달하거나 함수에서 값으로 반환할 수 있다.
이를 통해 프로그래밍의 유연성과 표현력을 높일 수 있다.

JavaScript에서 함수는 일급 객체로 간주되는데 즉, 언어의 다른 값이나 객체처럼 취급될 수 있다. 이것은 프로그래밍에서 더 큰 유연성과 표현력을 허용한다.

다음은 JavaScript에서 함수가 어떻게 일급 객체인지에 대한 몇 가지 예

1. 변수에 기능을 할당할 수 있다.

```javascript
const myFunc = function() {
  console.log("Hello world!");
};
```

2. 함수는 다른 함수에 대한 인수로 전달될 수 있다.

```javascript
function greet(name, greetingFunc) {
  console.log(greetingFunc(name));
}

function sayHello(name) {
  return "Hello " + name + "!";
}

greet("Alice", sayHello); // outputs "Hello Alice!"
```

3. 함수는 다른 함수의 값으로 반환될 수 있다.

```javascript
function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

const add5 = makeAdder(5);
console.log(add5(3)); // outputs 8
```

위 예제에서 함수는 언어의 다른 값이나 객체처럼 취급되며 다양한 방식으로 조작될 수 있다.

## Lifting State Up

상태 올리기(Lifting State Up)는 하위 구성 요소의 상태를 상위 구성 요소로 이동하는 React의 기술이다.
이를 통해 여러 하위 구성 요소가 동일한 상태를 공유하고 중앙 위치에서 상태를 업데이트할 수 있다.

```js
function ParentComponent() {
  const [count, setCount] = useState(0);

  function incrementCount() {
    setCount(count + 1);
  }

  return (
    <div>
      <ChildComponent count={count} incrementCount={incrementCount} />
      <AnotherChildComponent count={count} />
    </div>
  );
}

function ChildComponent(props) {
  return (
    <div>
      <p>Count: {props.count}</p>
      <button onClick={props.incrementCount}>Increment</button>
    </div>
  );
}

function AnotherChildComponent(props) {
  return <p>Count: {props.count}</p>;
}
```

위 예제에서 count 상태는 ParentComponent에 저장되고 ChildComponent 및 AnotherChildComponent에 소품(props)으로 전달된다.
incrementCount 함수도 ChildComponent에 소품(props)으로 전달되어 상위 구성 요소의 상태를 업데이트할 수 있다.

상위 구성 요소까지 상태를 들어 올리면 여러 하위 구성 요소가 동일한 상태를 공유할 수 있으며 중앙 위치에서 상태 업데이트를 처리할 수 있다.
이를 통해 코드를 보다 체계화하고 유지 관리하기 쉽게 만들 수 있으며 일관성 없는 상태로 인해 발생하는 버그의 위험을 줄일 수 있다.
