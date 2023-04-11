# React

## React란?

사용자 인터페이스를 만들기 위한 JavaScript 라이브러리

## React 컴포넌트

아래 함수는 데이터를 가진 하나의 `props` (`properties`의 짧은 표현) 객체 인자를 받은 후 React 엘리먼트를 반환하므로 유효한 React 컴포넌트입니다.

```typescript
export default function Greeting({name}: {name: string}) {
 return (
  <p>Hello, {name}</p>
 );
}
```

## React 리렌더링

리엑트가 리렌더링 되는 조건은 state(상태)값이 변경이 되었을 때 리렌더링이 발생한다.

React는 Virtual DOM을 이용하여 이전 VDOM 스냅샷과 현재 VDOM 스냅샷을 비교하여 변경된 부분만
업데이트를 진행한다.

- 참고
[React 렌더링 동작에 대한 (거의) 완벽한 가이드](https://velog.io/@superlipbalm/blogged-answers-a-mostly-complete-guide-to-react-rendering-behavior)
[React는 컴포넌트를 언제 다시 리렌더링 할까요?](https://velog.io/@surim014/react-rerender)

## IoC(Inversion of Control)

제어 역전이란 무엇일까?
가장 간단히 설명하자면 용어 그대로 코드의 로직이
일반적인 제어 흐름이 아니라 역전된 것을 의미한다.

`우리는 React 환경에서 view가 무엇을 하는지 정의하지 않고 (명령형) view가 어떻게 보일지를 선언한다.(선언형)`

- 참고 블로그
[프론트엔드에서의 Inversion of Control](https://tecoble.techcourse.co.kr/post/2021-05-14-inversion-of-control/)

위의 블로그에서 해당 내용에 대해서 참고하였는데 제어의 역전을 공부하다보니 명령형 프로그래밍과
선언형 프로그래밍을 알아보게 되고 추상화 등등... 생각해봐야 할 부분들이 많은 것 같다.

> 명령형(절차적) 프로그래밍은 당신이 어떤 일을 어떻게 할 것인가에 관한 것이고,
> 선언적 프로그래밍은 당신이 무엇을 할 것인가에 관한 것입니다.

- 참고 블로그
[명령형 vs 선언형 프로그래밍](https://iborymagic.tistory.com/73)

## Library VS Framework

### Library

- 라이브러리는 개발자가 특정 작업을 수행하기 위해 재사용할 수 있는 미리 작성된 코드 모음이다.
- 개발자가 코드를 완전히 제어할 수 있고 언제 어떤 라이브러리를 사용할지 결정할 수 있다.

### Framework

- 프레임워크는 개발자가 애플리케이션을 구축하는 방법에 대한 구조와 일련의 규칙을 제공하는 보다 포괄적인 도구입니다.
- 일반적으로 프레임워크에는 사용자 인증, 데이터베이스 액세스 및 라우팅과 같은 일반적인 작업을 처리하기 위한 사전 정의된 아키텍처, 프로그래밍 패러다임 및 구성 요소가 포함됩니다.
