# JSX

`JSX(JavaScript XML)는 Javascript에 XML을 추가한 확장한 문법이다.`

## React에서 JSX를 사용하는 목적

근본적으로, `JSX`는 `React.createElement(component, props, ...children)` 함수에 대한 문법적 설탕을 제공할 뿐입니다.

```javascript
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);

const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);

두 예시는 동일한 결과값을 나타내줍니다.

```

하지만 `React.createElement`로 작성하였을 때 보다 `JSX`를 사용하는 것이 훨씬 직관적이고 가독성이 좋고
`JSX`는 하나의 파일에 자바스크립트와 HTML을 동시에 작성하여 편리하다.

## Syntactic sugart

`직관적이지는 않지만 코드의 양을 줄일 수 있는 문법적인 설탕을 의미한다.`

### 대표적인 Syntactic sugar

#### 1. Ternary Operator(삼항 연산자)

```javascript
  삼항 연산자 사용 전

  setProviderList(prev => prev.map(item => (
    if (item.id === search.provider) {
      return { ...item, isChecked: !item.isChecked }
    } else {
      return item
    }
  )));


  삼항 연산자 사용 후

  setProviderList(prev => prev.map(item => (
    item.id === search.provider ? { ...item, isChecked: !item.isChecked } : item
  )));

  삼항 연산자를 사용하게 되면 사용 전보다 훨씬 간결하게 작성이 가능하다.

```

#### 2. Object Spread / Array Spread (객체 전개 / 배열 전개)

```javascript
  setProviderList(prev => prev.map(item => (
    item.id === search.provider ? { ...item, isChecked: !item.isChecked } : item
  )));

  위의 map 안에서 객체의 일부분을 변경하고 싶을 때 { ...item, isChecked: !item.isChecked }
  와 같이 기존의 객체안의 값을 전개하고 변경하고자 하는 값을 변경한다.

  const DEFAULT_CONFIG = {
    preserveWhitespace: true,
    noBreaks: false,
    foo: "bar",
  };

  const USER_CONFIG = {
    noBreaks: true,
  }

  const config = { ...DEFAULT_CONFIG, ...USER_CONFIG };

  위와 같이 두 객체를 모두 전개해서 하나의 객체로 변경하는 것도 가능하다. 이때 같은 key 값에 value가
  다를 경우 뒤에 들어오는 객체의 값으로 변환된다.

  배열도 객체의 예제와 동일하게 전개 후 하나의 배열로 병합하는게 가능하다. 다만 배열의 경우는 key가 없기
  때문에 각각 다른 배열을 전개해서 병합 할 때 중복되는 값도 모두 들어가게 된다.

  const arr1 = ['a', 'b', 'c'];
  const arr2 = ['c', 'd', 'e'];
  const arr3 = [...arr1, ...arr2];
  // console.log(arr3) => ['a', 'b', 'c', 'c', 'd', 'e']
```

#### 3. Object Destructuring / Array Destructuring (객체 구조 분해 할당 / 배열 구조 분해 할당)

```javascript
  export default function LectureBody({ classroomLecture }: Props): ReactElement {

    const {
      moduleList, classroomId, lastSectionId, lastSectionType,
    } = classroomLecture;
  ...
  }

  컴포넌트 props로 전달받은 객체를 구조 분해하여 필요한 값만 사용할 수 있다.

  // 이름과 성을 요소로 가진 배열
  let arr = ["Bora", "Lee"]

  // 구조 분해 할당을 이용해
  // firstName엔 arr[0]을
  // surname엔 arr[1]을 할당하였습니다.
  let [firstName, surname] = arr;

  배열도 마찬가지로 구조 분해하여 변수로 할당하여 사용 할 수 있다.

  // 두 번째 요소는 필요하지 않음
  let [firstName, , title] = ["Julius", "Caesar", "Consul", "of the Roman Republic"];

  alert( title ); // Consul

  추가로 필요하지 않은 배열의 값은 쉼표를 사용하여 요소를 버릴 수 있다.
```

#### 4. Object Rest / Array Rest (객체 나머지 연산자, 배열 나머지 연산자)

```javascript
  const {
    moduleList, classroomId, lastSectionId, lastSectionType, ...rest,
  } = classroomLecture;

  let [name1, name2, ...rest] = ['a', 'b', 'c', 'c', 'd', 'e'];

  console.log(rest); // ['c', 'c', 'd', 'e'];

  rest는 나머지 배열 요소들이 저장된 새로운 배열이 됩니다.
  rest 대신에 다른 이름을 사용해도 되는데, 변수 앞의 점 세 개(...)와 변수가 가장 마지막에 위치해야 한다.

  function sum(...theArgs) {
    let total = 0;
    for (const arg of theArgs) {
      total += arg;
    }
    return total;
  }

  console.log(sum(1, 2, 3));
  // Expected output: 6

  console.log(sum(1, 2, 3, 4));
  // Expected output: 10

  함수의 매개변수를 전달 할때도 사용이 가능하다.
```

## React.createElement

`React.createElement`는 `React`에서 가장 기본적인 컴포넌트 생성 방법 중 하나입니다. 이 함수를 사용하여 React 요소를 생성하고 이를 렌더링할 수 있다.

`React.createElement` 함수는 세 개의 인수가 필요하다.

1. 요소의 유형 (문자열 또는 컴포넌트 함수)
2. 요소의 속성 (또는 "props") 또는 null
3. 자식 요소들

```javascript
React.createElement('div', { className: 'test' }, 'Hello, World!')
```

위 코드는 아래와 같은 React 요소를 만들어낸다.

```javascript
<div className="test">Hello, World!</div>
```

`React.createElement` 함수는 컴포넌트 함수를 첫 번째 인수로 사용할 수도 있다.
이 경우 함수 이름을 문자열로 전달하거나 ES6의 화살표 함수 구문을 사용하여 직접 함수를 전달할 수 있습니다. 또한 속성 및 자식 요소들은 컴포넌트 함수의 인수로 전달됩니다.

```javascript
function MyComponent(props) {
  return React.createElement('div', { className: 'test' }, props.message);
}

React.createElement(MyComponent, { message: 'Hello, World!' });
```

```javascript
<div className="test">Hello, World!</div>
```

## React Element

```typescript
interface ReactElement<P = any, T extends string | JSXElementConstructor<any> = string | JSXElementConstructor<any>> {
  type: T;
  props: P;
  key: Key | null;
}
```

`React Element`의 속성(property)

- type: 요소의 유형, 예를 들어 "div" 또는 사용자 지정 컴포넌트 함수입니다.
- props: 요소의 속성, 예를 들어 className, style, onClick 등의 속성이 포함됩니다.
- key: 컴포넌트가 업데이트될 때 React가 요소를 식별하는 데 사용되는 고유한 식별자입니다.
- ref: React 요소에 대한 참조(reference)를 만드는 데 사용됩니다.

`React`에서 렌더링되는 가장 작은 단위이다.
`React Element`는 `JavaScript` 객체로, `React` 요소를 나타낸다.
`React` 요소는 화면에 렌더링되는 요소를 나타내며, 다른 `React` 요소들과 결합하여 `React` 컴포넌트를 만드는 데 사용된다.

`React Element`는 불변객체(immutable object)이며, 한 번 생성되면 수정될 수 없습니다. 이러한 불변성은 `React`의 성능을 향상시키는 데 기여합니다. `React`는 변화가 필요한 경우 새로운 `React Element`를 만들고 기존의 `Element`와 새 `Element`를 비교하여 최소한의 변경만 적용하므로 렌더링 성능을 향상시킵니다.

## React StrictMode

애플리케이션에서 잠재적인 문제를 미리 감지하고 해결할 수 있도록 도와주는 도구
StrictMode는 개발 모드에서만 동작하며, 브라우저에서는 아무런 영향을 미치지 않는다.

`StrictMode를 통해서 얻을 수 있는 효과`

- `부수효과 검사`: React 컴포넌트에서 부수효과(일반적으로 생명주기 메서드, useEffect 등)를 사용할 때 경고 메시지를 출력하여 잠재적인 문제를 감지할 수 있다.

- `레거시 문자열 ref 경고`: 문자열을 사용하여 ref를 생성하면 경고 메시지가 표시됩니다. 문자열 ref는 더 이상 권장되지 않으며, 함수를 사용하여 ref를 생성하는 것이 좋다.

- `레거시 생명주기 메서드 경고`: 레거시 생명주기 메서드(componentWillMount, componentWillReceiveProps, componentWillUpdate)를 사용하면 경고 메시지가 표시됩니다. 이러한 메서드는 더 이상 권장되지 않으며, 대신에 componentDidMount, componentDidUpdate, getDerivedStateFromProps 및 getSnapshotBeforeUpdate 메서드를 사용하는 것이 좋다.

- `안전하지 않은 생명주기 메서드 경고`: 안전하지 않은 생명주기 메서드(UNSAFE_componentWillMount, UNSAFE_componentWillReceiveProps, UNSAFE_componentWillUpdate)를 사용하면 경고 메시지가 표시됩니다. 이러한 메서드는 향후 `React` 업데이트에서 삭제될 예정이며, 대신에 getDerivedStateFromProps 및 getSnapshotBeforeUpdate 메서드를 사용하는 것이 좋다.

StrictMode를 사용하면 애플리케이션에서 발생할 수 있는 잠재적인 문제를 조기에 감지할 수 있으므로,
`React` 애플리케이션의 개발 및 유지보수를 보다 안전하게 수행할 수 있다.

## VDOM(Virtual DOM)이란?

`Virtual DOM`(가상 DOM)은 `React`의 핵심 개념 중 하나입니다. `Virtual DOM`은 브라우저가 직접 조작하는 실제 `DOM`과는 별도로, JavaScript 객체로 이루어진 객체 모델이다.

`React`에서 컴포넌트가 업데이트될 때, 실제 `DOM`을 조작하는 것이 아니라, `Virtual DOM`을 업데이트하고, 이전과 새로운 `Virtual DOM`을 비교하여 변경된 부분만 실제 `DOM`에 적용합니다. 이를 통해 `DOM` 조작 횟수를 최소화하고, 빠른 렌더링을 구현할 수 있습니다.

`React`에서는 이러한 `Virtual DOM`을 구현하고, 각 컴포넌트의 상태와 속성이 변경될 때마다 `Virtual DOM`을 업데이트하고, 변경된 부분만 최적화된 방식으로 실제 `DOM`에 적용하여 UI를 업데이트합니다. 이를 통해 `React`는 빠르고 안정적인 UI 개발을 가능케 합니다.

### DOM이란?

`DOM`(Document Object Model)은 웹 페이지의 구조화된 내용을 표현하는 객체 모델입니다.
즉, HTML, XML 또는 XHTML 문서를 브라우저가 이해할 수 있는 객체 모델로 변환하여, 자바스크립트를 사용하여 문서의 구조, 스타일, 콘텐츠 등을 동적으로 조작할 수 있게 합니다.

`DOM`은 브라우저에서 웹 페이지의 HTML 문서를 로드하고 파싱한 결과물을 나타내는 객체 모델입니다.
HTML 문서를 이루는 모든 요소들은 객체로 표현되며, 이러한 객체들은 서로 계층적인 관계를 가지고 있습니다. 이렇게 만들어진 객체 모델을 통해 개발자는 웹 페이지의 각 요소에 접근하고 조작할 수 있습니다.

### DOM과 Virtual DOM의 차이

`DOM`은 실제로 브라우저에서 웹 페이지를 렌더링하는 데 사용되는 객체 모델입니다. 브라우저가 HTML, CSS, JavaScript를 로드하고 해석한 결과물을 나타내는 객체 모델이며, 이를 통해 개발자가 자바스크립트를 사용하여 웹 페이지의 동적인 요소를 조작할 수 있습니다. `DOM`은 브라우저에서 직접 조작되는 실제 객체이므로, `DOM` 조작 작업은 브라우저의 성능을 크게 저하시킬 수 있습니다.

반면, `Virtual DOM`은 JavaScript 객체로 이루어진 객체 모델로서, `React`에서 UI 렌더링에 사용됩니다. `React`는 `Virtual DOM`을 사용하여, 컴포넌트의 상태와 속성이 변경될 때마다 `Virtual DOM`을 업데이트하고, 변경된 부분만 최적화된 방식으로 실제 DOM에 적용하여 UI를 업데이트합니다. `Virtual DOM`은 `React`에서 내부적으로 관리되는 것으로, 브라우저가 직접 조작하지 않으므로 DOM 조작 작업의 비용을 크게 절감할 수 있습니다.

### Reconciliation(재조정) 과정은 무엇인가?

React에서 Reconciliation(재조정)은 `Virtual DOM`에서 이루어지는 과정으로, 이전 상태와 현재 상태의 `Virtual DOM`을 비교하여 변경된 부분만 실제 DOM에 업데이트하는 과정입니다.

Reconciliation은 `Virtual DOM`의 노드를 순회하며 이전 상태와 비교하여 변경된 부분을 찾습니다. 이 과정에서 React는 효율적으로 비교를 수행하기 위해 다양한 최적화 기술을 사용합니다. 예를 들어, 같은 컴포넌트가 여러 번 렌더링될 때, React는 이전 렌더링 결과와 현재 렌더링 결과를 비교하여 변경된 부분만 업데이트합니다.

Reconciliation의 이점은 성능과 사용자 경험 개선입니다. React는 `Virtual DOM`을 사용하여 변경된 부분만 렌더링하므로, 필요한 최소한의 DOM 조작만 수행되어 성능이 향상됩니다. 또한, 변경된 부분만 업데이트되므로, 불필요한 화면 깜빡임을 방지하고 사용자 경험을 개선할 수 있습니다.

#### Aha Moment

전개 구문에 대해서 MDN을 확인했을 때 아래와 같은 내용을 추가로 확인 할 수 있었다.

`apply()` 대체

일반적으로 배열의 엘리먼트를 함수의 인수로 사용하고자 할 때 `Function.prototype.apply()` 를 사용하였습니다.

```javascript
  function myFunction(x, y, z) { }
  let args = [0, 1, 2];
  myFunction.apply(null, args);

  전개 구문을 사용해 위 코드는 다음과 같이 작성될 수 있습니다.

  function myFunction(x, y, z) { }
  let args = [0, 1, 2];
  myFunction(...args);
```

`배열 복사`

```javascript
  let arr = [1, 2, 3];
  let arr2 = [...arr]; // arr.slice() 와 유사
  arr2.push(4);

  // arr2 은 [1, 2, 3, 4] 이 됨
  // arr 은 영향을 받지 않고 남아 있음
```

`배열 병합`

```javascript
  let arr1 = [0, 1, 2];
  let arr2 = [3, 4, 5];
  // arr2 의 모든 항목을 arr1 에 붙임
  arr1 = arr1.concat(arr2);

  전개 구문을 사용하여 위와 동일하게 변경 할 수 있습니다.

  let arr1 = [0, 1, 2];
  let arr2 = [3, 4, 5];
  arr1 = [...arr1, ...arr2]; // arr1 은 이제 [0, 1, 2, 3, 4, 5]
```

`배열 병합 및 순서변경`

```javascript
  let arr1 = [0, 1, 2];
  let arr2 = [3, 4, 5];
  // arr2 의 모든 항목을 arr1 의 앞에 붙임
  Array.prototype.unshift.apply(arr1, arr2) // arr1 은 이제 [3, 4, 5, 0, 1, 2] 가 됨

  전개 구문을 사용하여 위와 동일하게 변경 할 수 있습니다.

  let arr1 = [0, 1, 2];
  let arr2 = [3, 4, 5];
  arr1 = [...arr2, ...arr1]; // arr1 은 이제 [3, 4, 5, 0, 1, 2] 가 됨
```

{% hint style="info" %}
 참고: unshift()와 달리, 전개 구문을 사용시에는 새로운 arr1을 만들며 기존 배열을 변형하지 않습니다.
{% endhint %}

전개 구문이 추가되고 나서 데이터의 불변성을 유지하기 더 용이해진 것 같다고 생각이 들었다.
추가로 전개 구문이 어디에서 파생되어져 왔는지 알 수 있는 시간이었다.

이번에 데브노트 키워드를 검색해보면서 느낀 부분은 `React`가 어떤 문제점을 해결하기 위해서 `JSX`를 도입하고 `VDOM`을 도입하게 되었는지 생각해보는 계기가 되었던 것 같다. 현재 실무에서 작업하면서도 이 기술이 왜 나오게 되었는지에 대해서 깊게 고민 해본적이 없고 대략적인 부분에 대해서만 알고 있었다면 이번에 `React`에 대한 전반적인 내용을 찾아보고 정리하면서 `React`와 전보다 더 가까워진 느낌이 들었다. 이번에 정리한 노트를 기반으로 지속적으로 머릿속에 집어 넣는 과정을 통해서 기본을 잘 기억하도록 해야겠다.

#### Reference

- [JSX 이해하기](https://ko.reactjs.org/docs/jsx-in-depth.html)
- [Destructuring](https://ko.javascript.info/destructuring-assignment)
- [Spread](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread_syntax)