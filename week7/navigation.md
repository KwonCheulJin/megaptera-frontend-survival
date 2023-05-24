# 4.Navigation

## Web APIs - History

웹 개발에서 History API는 개발자가 브라우저의 기록을 조작하고 상호 작용할 수 있도록 웹 브라우저에서 제공하는 메서드 및 속성 집합이다.
History API는 탐색 기록에 대한 액세스를 제공하여 개발자가 앞뒤로 탐색하고 URL을 수정하고 탐색 이벤트를 프로그래밍 방식으로 처리할 수 있도록 한다.

History API의 주요 구성 요소

1. 기록 개체(The history Object): 기록 API의 중심 개체는 브라우저의 세션 기록을 나타내는 기록 개체다.
window.history 속성을 통해 액세스할 수 있다.
기록 개체는 검색 기록을 탐색하고 상호 작용할 수 있는 메서드와 속성을 제공한다.

2. 기록 탐색(Navigating History): 기록 개체를 사용하면 사용자의 검색 기록을 탐색할 수 있다.

- 사용법
- go(): 주어진 매개변수를 기반으로 히스토리의 특정 지점으로 이동한다. 양수 값은 앞으로 이동하고 음수 값은 뒤로 이동한다. 예를 들어 history.go(-1)는 한 페이지 뒤로 이동한다.
- back(): history.go(-1)와 동일하며 한 페이지 뒤로 이동한다.
- forward(): history.go(1)와 동일하며 한 페이지 앞으로 이동한다.
- pushState(): 브라우저의 기록 스택에 새 항목을 추가한다. state(새 기록 항목과 관련된 상태 개체), unused(대부분의 브라우저에서 현재 무시되는 새 항목의 제목) 및 url(새 URL)의 세 가지 매개 변수를 사용한다.
- replaceState(): 현재 기록 항목을 새 항목으로 바꿉니다. pushState()와 동일한 매개변수를 사용하지만 새 항목을 만드는 대신 현재 항목을 바꿉니다.

3. 읽기 기록(Reading History): 기록 개체는 검색 기록에 대한 정보에 액세스할 수 있는 속성을 제공한다. 일반적으로 사용되는 일부 속성은 다음과 같다.

- length: 히스토리 스택의 항목 수를 반환한다.
- state: 현재 기록 항목과 관련된 상태 개체를 반환한다.

4. 내비게이션 이벤트 처리(Handling Navigation Events): History API를 사용하면 사용자가 새 페이지로 이동하거나 URL이 변경될 때와 같은 내비게이션 이벤트를 처리할 수도 있다.
PopStateEvent는 사용자가 go(), back() 또는 forward()와 같은 메서드를 사용하여 기록을 탐색할 때 트리거된다.
이 이벤트를 수신하여 그에 따라 작업을 수행하거나 UI를 업데이트할 수 있다.

5. URL 조작(Manipulating URLs): History API를 사용하면 페이지를 다시 로드하지 않고도 브라우저의 주소 표시줄에 표시된 URL을 수정할 수 있다.
앞에서 언급한 pushState() 및 replaceState() 메서드를 사용하면 전체 페이지를 다시 로드하지 않고도 URL을 변경하고 기록 항목을 추가/업데이트할 수 있다.

6. 호환성 및 제한(Compatibility and Limitations): History API는 최신 웹 브라우저에서 지원된다. 그러나 보안 문제로 인해 몇 가지 제한 사항이 있다.
예를 들어 보안상의 이유로 주소 표시줄에서 전체 URL을 직접 읽거나 수정할 수 없다. URL 경로, 쿼리 매개변수 및 조각만 수정할 수 있다.

## React Router - NavLink, Link, Navigate, useNavigate

React Router에서는 다음과 같은 네비게이션 컴포넌트들을 제공한다

- Link: HTML의 a 태그와 유사하지만 페이지 전환을 방지하는 기능이 내장되어 있다.
- NavLink: Link의 특수 버전으로, 특정 링크에 스타일을 넣어줄 수 있다.
- Navigate: 프로그래밍 방식으로 페이지를 이동할 수 있게 해주는 컴포넌트이다.
- useNavigate: 페이지 이동을 할 수 있게 해주는 훅이다.

Link와 NavLink는 다음과 같이 사용할 수 있다:

```js
import { Link, NavLink } from "react-router-dom";

<Link to="/about">About</Link>
```

```js
declare function Link(props: LinkProps): React.ReactElement;

interface LinkProps
  extends Omit<
    React.AnchorHTMLAttributes<HTMLAnchorElement>,
    "href"
  > {
  replace?: boolean;
  state?: any;
  to: To;
  reloadDocument?: boolean;
  preventScrollReset?: boolean;
  relative?: "route" | "path";
}

type To = string | Partial<Path>;

interface Path {
  pathname: string;
  search: string;
  hash: string;
}
```

```js
import { NavLink } from "react-router-dom";
<NavLink
  to={path}
  className={({ isActive, isPending }) =>
    isPending ? "pending" : isActive ? "active" : ""
  }
  style={({ isActive, isPending }) => {
    return {
      fontWeight: isActive ? "bold" : "",
      color: isPending ? "red" : "black",
    };
  }}
  >
  {({ isActive }) => (<SubItem id={sub.id} className={`${sub.id}${isActive ? ' active' : ''}`}>{sub.titleName}</SubItem>)}
</NavLink>
```

```js
export interface NavLinkProps extends Omit<LinkProps, "className" | "style" | "children"> {
    children?: React.ReactNode | ((props: {
        isActive: boolean;
        isPending: boolean;
    }) => React.ReactNode);
    caseSensitive?: boolean;
    className?: string | ((props: {
        isActive: boolean;
        isPending: boolean;
    }) => string | undefined);
    end?: boolean;
    style?: React.CSSProperties | ((props: {
        isActive: boolean;
        isPending: boolean;
    }) => React.CSSProperties | undefined);
}
```

Navigate와 useNavigate는 다음과 같이 사용할 수 있다

```js
import { Navigate, useNavigate } from "react-router-dom";

<Navigate to="/about" />
const navigate = useNavigate();
navigate("/about");
```
