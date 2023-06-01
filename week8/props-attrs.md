# 5.props와 attrs

## props

스타일 컴포넌트에서 스타일 컴포넌트에 추가 속성을 전달하는 두 가지 주요 방법에는 props와 attrs이라는 두 가지가 있다.

스타일 컴포넌트의 프로퍼티는 부모 컴포넌트로부터 컴포넌트로 전달되거나 컴포넌트 내에서 내부적으로 사용되는 프로퍼티를 의미한다. 이러한 소품은 스타일 정의 내에서 액세스하고 사용하여 동적 스타일을 만들 수 있다.

1. 보간(Interpolation): 템플릿 리터럴을 사용하여 스타일 정의 내에서 소품을 보간할 수 있다. 예를 들어 color라는 이름의 소품이 있는 경우 이를 사용하여 스타일이 지정된 컴포넌트의 색상 속성을 동적으로 설정할 수 있다.

`보간(Interpolation) - 알려진 지점의 값 사이(중간)에 위치한 값을 알려진 값으로부터 추정하는 것을 말한다.`

```js
const Button = styled.button`
  color: ${props => props.color};
`;
```

2. 조건부 스타일링(Conditional Styling): 소품을 사용하여 특정 조건에 따라 스타일을 조건부로 적용할 수 있다. 예를 들어 isPrimary라는 소품의 값에 따라 버튼의 배경색을 변경할 수 있다.

```js
const Button = styled.button`
  background-color: ${props => props.isPrimary ? 'blue' : 'gray'};
`;
```

## attrs

스타일이 지정된 컴포넌트의 attrs 메서드를 사용하면 스타일링과 관련이 없는 추가 속성을 컴포넌트에 전달할 수 있다.
이러한 속성은 정적 값일 수도 있고 컴포넌트 소품에서 파생된 동적 값일 수도 있다.

1. 정적 속성(Static Attributes): attrs 메서드를 사용하여 스타일 컴포넌트에 정적 속성을 전달할 수 있다. 컴포넌트가 렌더링하는 기본 DOM 요소에 추가 어트리뷰트를 첨부하려는 경우 유용할 수 있다.

```js
const Link = styled.a.attrs({
  target: "_blank",
  rel: "noopener noreferrer",
})`
  color: blue;
`;
```

이 예제에서 링크 컴포넌트는 대상 및 rel 속성이 각각 "_blank" 및 "noopener noreferrer"로 설정된 `<a>` 태그로 렌더링된다.

2. 동적 속성(Dynamic Attributes): attrs 메서드를 사용하여 컴포넌트 소품을 기반으로 동적 속성을 전달할 수도 있다. 이를 통해 특정 조건에 따라 조건부로 속성을 첨부할 수 있다.

```js
const Button = styled.button.attrs(props => ({
  disabled: props.isLoading,
}))`
  background-color: ${props => props.isPrimary ? 'blue' : 'gray'};
`;
```

이 예제에서 버튼 컴포넌트는 isLoading 프로퍼티에 따라 비활성화 속성이 설정된다. isLoading이 참이면 버튼이 비활성화된다.

중요한 점은 attrs 메서드는 컴포넌트 자체의 스타일링에 영향을 주지 않는다는 것이다. 주로 스타일이 지정된 컴포넌트가 렌더링하는 기본 DOM 요소에 추가 어트리뷰트를 첨부하는 데 사용된다.

props와 attrs를 사용하면 컴포넌트의 프로퍼티 및 기타 요소에 따라 스타일과 속성을 모두 동적으로 조정하여 스타일이 적용된 컴포넌트의 유연성과 재사용성을 향상시킬 수 있다.
