# Testing Library

## Jest

- 페이스북에서 만든 테스팅 도구이다.
- 테스팅 프레임워크의 최초 사용자들에게 많은 설정을 요구하지는 않는다.(zero config)

## Describe-Context-It 패턴

|키워드|설명|
|---|---|
|Describe|설명할 테스트 대상을 명시한다.|
|Context|테스트 대상이 놓인 상황을 설명한다.|
|It|테스트 대상의 행동을 설명한다.|

### 장점

- 테스트 코드를 계층 구조로 만들어 준다.
- "빠뜨린" 테스트 코드를 찾기 쉽다.

```typescript
describe('add 함수는', () => {
  it('두 숫자의 합을 리턴해준다.', () => {
    expect(add(1, 2)).toBe(3);
  });
});
```

앞으로 진행되는 강의의 테스트 코드를 작성할 때 해당 구조로 작성을 진행해 봐야겠다.

## React Testing Library

> The more your tests resemble the way your software is used,
> the more confidence they can give you. - RTL 공식문서
> 테스트가 소프트웨어 사용 방식과 유사할수록 더 많은 신뢰를 얻을 수 있습니다.

React Testing Library는 UI에 특화된 라이브러리이다.

> RTL은 이름 그대로 React 컴포넌트를 테스트 하기 위해 만들어진 도구이기 때문에,
> 기본적으로 CRA에 내장되어 있습니다. 만약 CRA를 사용하지 않고 개발 환경을 직접 설정한다면
> `npm install --save-dev @testing-library/react` 명령어를 이용해 설치하면 됩니다.

```typescript
test('Greeting', () => {
 render(<Greeting name='world' />);

 const text = screen.getByText(/Hello, world/);
 expect(text).toBeInTheDocument();
});
```

### 쿼리 타입

- get - 동기적으로 처리되며 타겟을 찾지 못할 시 에러를 던집니다.
- find - 비동기적으로 처리되며 타겟을 찾지 못할 시 에러를 던집니다.
- query - 동기적으로 처리되며 타겟을 찾지 못할 시 null을 반환합니다.

Action, Assertion, 비동기 테스트 등등 이 부분도 앞으로 강의가 진행되면서 무분별한 테스트를
작성하기 보다 정말 필요한 부분에 테스트가 들어가도록 고민하면서 진행해 봐야 할 것 같다.

- 참고
[초심자를 위한 React Testing Library](https://tecoble.techcourse.co.kr/post/2021-10-22-react-testing-library/)
