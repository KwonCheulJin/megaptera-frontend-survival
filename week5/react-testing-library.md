# 2.React Testing Library

## React Testing Library

`React Testing Library`는 사용자가 상호 작용하는 방식을 시뮬레이션하는 방식으로 React 구성 요소를 테스트하는 간단하고 직관적인 방법을 제공하는 테스트 유틸리티이다.
이는 사용자가 웹 애플리케이션과 상호 작용하는 방식과 유사한 방식으로 DOM을 쿼리하고 조작하기 위한 유틸리티 세트를 제공하는 DOM 테스팅 라이브러리 위에 구축된다.

`React Testing Library`는 개발자가 구현 세부 사항이 아닌 구성 요소의 동작에 초점을 맞춘 테스트를 작성하도록 권장하는 것을 목표로 한다.
즉, 특정 요소나 스타일의 존재와 같은 특정 구현 세부 정보를 테스트하는 대신 구성 요소가 사용자 상호 작용 및 해당 상태 변경에 대한 응답으로 올바르게 작동하는지 확인하기 위해 테스트를 작성해야 한다.

`React Testing Library`는 `DOM`을 쿼리하고 `render`, `fireEvent` 및 `waitFor`와 같은 구성 요소와 상호 작용하기 위한 일련의 유틸리티를 제공한다.
이러한 유틸리티를 통해 개발자는 단추 클릭 또는 양식에 텍스트 입력과 같은 구성 요소와의 사용자 상호 작용을 시뮬레이션하고 이러한 상호 작용에 대한 응답으로 구성 요소가 올바르게 작동하는지 확인할 수 있다.

`React Testing Library`를 사용하면 개발자가 React 구성 요소에 대해 보다 안정적이고 유지 관리 가능한 테스트를 작성하는 동시에 보다 사용자 중심적인 테스트 접근 방식을 촉진할 수 있다.
구현 세부 사항이 아닌 구성 요소의 동작에 초점을 맞춤으로써 개발자는 구성 요소의 내부 구조 변경에 더 탄력적이고 최종 사용자의 요구와 기대에 더 잘 부합하는 테스트를 작성할 수 있다.

> The more your tests resemble the way your software is used,
> the more confidence they can give you. - RTL 공식문서
> 테스트가 소프트웨어 사용 방식과 유사할수록 더 많은 신뢰를 얻을 수 있습니다.

React Testing Library는 UI에 특화된 라이브러리이다.

> RTL은 이름 그대로 React 컴포넌트를 테스트 하기 위해 만들어진 도구이기 때문에,
> 기본적으로 CRA에 내장되어 있습니다. 만약 CRA를 사용하지 않고 개발 환경을 직접 설정한다면
> `npm install --save-dev @testing-library/react` 명령어를 이용해 설치하면 된다.

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
- query - 동기적으로 처리되며 타겟을 찾지 못할 시 null을 반환한다.

Action, Assertion, 비동기 테스트 등등 이 부분도 앞으로 강의가 진행되면서 무분별한 테스트를
작성하기 보다 정말 필요한 부분에 테스트가 들어가도록 고민하면서 진행해 봐야 할 것 같다.

- 참고
[초심자를 위한 React Testing Library](https://tecoble.techcourse.co.kr/post/2021-10-22-react-testing-library/)

## Given-When-Then 패턴

GWT(Given-When-Then) 패턴은 소프트웨어 테스트를 보다 이해하기 쉽고 유지 관리하기 쉽게 구성하는 방법이다.
이 패턴은 행동 기반 개발(BDD) 및 승인 테스트에서 일반적으로 사용되지만 단위 테스트 및 기타 형태의 자동 테스트에도 적용될 수 있다.

GWT 패턴은 세 부분으로 구성된다.

1. Given: 이 섹션에서는 테스트의 전제 조건을 설명한다. 테스트 중인 시스템 또는 응용 프로그램의 상태를 정의하여 테스트가 실행될 컨텍스트를 설정한다.
2. When: 이 섹션에서는 테스트 중인 동작을 트리거하는 작업 또는 이벤트를 설명한다. 이는 테스트 중인 특정 입력 또는 작업을 나타내며 종종 테스트 중인 시스템에서 함수 또는 메서드를 호출하는 것과 관련된다.
3. Then: 이 섹션에서는 테스트의 예상 결과 또는 동작을 설명한다. 이전 단계에서 정의된 입력 또는 작업을 기반으로 예상되는 출력 또는 동작을 지정한다.

```js
describe('sum function', () => {
  test('Given two positive numbers, when the sum function is called with those numbers, then the result should be the sum of the two numbers', () => {
    // Given
    const a = 2;
    const b = 3;

    // When
    const result = sum(a, b);

    // Then
    expect(result).toBe(5);
  });
});
```

GWT 패턴을 사용하면 소프트웨어 테스트를 따라하기 쉬운 개별 단계로 나누어 소프트웨어 테스트를 더 쉽게 작성하고 이해할 수 있다.
또한 각 테스트에 대한 특정 입력, 작업 및 예상 결과를 쉽게 식별할 수 있으므로 향후 테스트를 디버깅하거나 유지 관리할 때 유용할 수 있다.

## Mocking

모킹은 코드 단위를 격리하고 테스트하기 위해 코드 단위가 의존하는 복잡한 시스템 또는 구성 요소의 동작을 시뮬레이션하기 위해 소프트웨어 테스트에 사용되는 기술이다.
이 기술에는 실제 개체의 동작을 모방하는 가짜 개체를 만들고 이를 사용하여 테스트 중에 실제 개체를 대체하는 작업이 포함된다.

모킹 프로세스에는 실제 개체의 동작을 시뮬레이션하지만 단순화되거나 미리 결정된 동작을 사용하는 모의 개체를 만드는 과정이 포함된다.
그런 다음 모의 개체는 테스트 중인 단위의 컨텍스트에서 실제 개체의 동작을 시뮬레이션하는 데 사용되며 테스트 결과는 모의 개체의 동작을 기반으로 평가된다.

테스트에서 조롱을 사용하면 다음과 같은 몇 가지 이점이 있다.

1. 격리(Isolation): 복잡한 외부 종속성을 모의 개체로 대체하면 외부 시스템의 동작에 대해 걱정할 필요 없이 코드를 격리하여 테스트할 수 있다.
2. 제어(Control): 모의 개체는 특정 동작이나 응답을 시뮬레이션하도록 프로그래밍할 수 있으므로 테스트 중인 시스템의 입력과 출력을 제어할 수 있다.
3. 속도(Speed): 모킹을 사용하면 외부 리소스의 필요성을 줄이고 테스트를 더 빠르게 실행할 수 있으므로 테스트 속도를 높일 수 있다.

```js
import axios from 'axios';

function fetchData(url) {
  return axios.get(url)
    .then(response => response.data)
    .catch(error => console.error(error));
}

test('fetchData should return the correct data', () => {
  const mockData = { id: 1, name: 'John' };
  const mockedAxios = jest.spyOn(axios, 'get').mockResolvedValue({ data: mockData });

  return fetchData('/api/data')
    .then(data => {
      expect(data).toEqual(mockData);
      expect(mockedAxios).toHaveBeenCalledWith('/api/data');
    });
});
```

이 예에서는 axios 라이브러리를 사용하여 외부 API에서 데이터를 가져오는 fetchData라는 함수를 테스트하고 있다.
fetchData 함수의 동작을 분리하기 위해 Jest 모형을 사용하여 axios 라이브러리의 동작을 시뮬레이트한다.

axios.get 함수를 대체하는 데 사용할 수 있는 새로운 모의 함수를 생성하는 jest.spyOn 함수를 사용하여 axios에 대한 모의 개체를 만든다.
그런 다음 mockResolvedValue 함수를 사용하여 모의 함수가 호출될 때 반환해야 하는 값을 설정한다.

테스트에서 모의 ​​URL로 fetchData 함수를 호출하고 expect 함수를 사용하여 함수가 올바른 데이터를 반환하는지 확인한다.
또한 toHaveBeenCalledWith 함수를 사용하여 모의 axios.get 함수가 올바른 URL로 호출되었음을 확인한다.

테스트에서 모의를 사용하여 외부 axios 라이브러리의 동작에 대해 걱정할 필요 없이 fetchData 함수의 동작을 격리하고 테스트할 수 있다.

## Test fixture

Test fixture는 하나 이상의 테스트의 기반으로 사용되는 시스템의 고정 상태이다.
특정 코드 조각을 테스트하기 위한 알려진 시작점을 제공하는 설정이며 테스트 중인 코드가 알려진 조건에서 일관되게 동작하도록 설계되었다.

Test fixture에는 일반적으로 테스트를 실행하는 데 필요한 데이터, 개체 또는 기타 리소스를 비롯한 테스트 환경 설정이 포함된다. 여기에는 데이터베이스 초기화, 파일 시스템 설정, 테스트 데이터 생성 및 모의 개체 설정이 포함될 수 있다.

Test fixture의 목적은 코드를 테스트할 수 있는 알려진 통제된 환경을 만들고 외부 요인이 테스트 결과에 영향을 미칠 가능성을 최소화하는 것이다. 이를 통해 개발자는 코드를 보다 정확하고 효율적으로 테스트하고 문제나 이슈가 더 심각해지기 전에 문제를 식별할 수 있다.

단위 테스트에서 Test fixture는 일반적으로 각 테스트 사례에 대해 생성되며 코드를 테스트하는 데 필요한 조건을 설정하는 데 사용된다. 이렇게 하면 각 테스트가 일관된 환경에서 실행되고 결과를 정확하게 비교할 수 있다.

```js
describe('sum function', () => {
  let a, b;

  beforeEach(() => {
    a = 2;
    b = 3;
  });

  test('should return the sum of two numbers', () => {
    const result = sum(a, b);
    expect(result).toBe(5);
  });

  test('should return a number', () => {
    const result = sum(a, b);
    expect(typeof result).toBe('number');
  });
});
```

이 예제에서는 두 개의 숫자를 인수로 받아 합계를 반환하는 합산 함수를 테스트하고 있다.
각 테스트가 실행되기 전에 테스트 픽스처를 사용하여 a와 b의 값을 설정하여 합계 함수를 테스트하기 위한 알려진 시작점을 확보하고 있다.

각 테스트가 실행되기 전에 beforeEach 함수를 사용하여 a와 b의 값을 설정한다.
이렇게 하면 각 테스트에 대해 동일한 입력과 설정으로 일관된 환경에서 테스트를 실행할 수 있다.

그런 다음 Jest에서 제공하는 테스트 함수를 사용하여 두 개의 테스트 케이스를 정의한다.
각 테스트 케이스는 합계 함수를 사용하여 a와 b의 합계를 계산하고, 기대 함수를 사용하여 합계 함수의 동작에 대한 어설션을 만든다.

## 5주차 테스트를 마치면서

위의 키워드들이 테스트를 하면서 효율있게 테스트를 작성하는데 많은 도움을 주는 것을 느끼게 되었다.
앞으로 테스트를 더 많이 진행해 봐야 알겠지만 5주차 과제를 진행하면서 mocking 작업 및 컴포넌트 내에서 사용하는 hooks를 어떻게 테스트에 잘 연결시켜 줄 것인지에 대해서도
많이 고민하게 되었던 시간이었다.
아직은 어렵지만 지속하다보면 더 좋은 구조와 좋은 컴포넌트 작성이 될 것 같다.
