# 5.usehooks-ts

## [usehooks-ts](https://usehooks-ts.com/)

### [useBoolean](https://usehooks-ts.com/react-hook/use-boolean)

- A simple abstraction to play with a boolean, don't repeat yourself.
(부울을 가지고 놀기 위한 간단한 추상화, 반복하지 마세요.)

### [useEffectOnce](https://usehooks-ts.com/react-hook/use-effect-once)

- Just modified version of useEffect that's executed only one time, at the mounting time.
(마운팅 시점에 한 번만 실행되는 사용 효과의 수정된 버전입니다.)

### [useFetch](https://usehooks-ts.com/react-hook/use-fetch)

- Here is a React Hook which aims to retrieve data on an API using the native Fetch API.
  (다음은 네이티브 Fetch API를 사용하여 API에서 데이터를 검색하는 것을 목표로 하는 React Hook입니다.)
- I used a reducer to separate state logic and simplify testing via functional style.
  (상태 로직을 분리하고 함수형 스타일을 통해 테스트를 단순화하기 위해 리듀서를 사용했습니다.)
- The received data is saved (cached) in the application via useRef, but you can use LocalStorage (see useLocalStorage()) or a caching solution to persist the data.
  (수신된 데이터는 useRef를 통해 애플리케이션에 저장(캐시)되지만, 데이터를 지속시키기 위해 LocalStorage(useLocalStorage() 참조) 또는 캐싱 솔루션을 사용할 수 있습니다.)
- The fetch is executed when the component is mounted and if the url changes.
If ever the url is undefined, or if the component is unmounted before the data is recovered, the fetch will not be called.
  (컴포넌트가 마운트되고 URL이 변경되면 가져오기가 실행됩니다. URL이 정의되지 않았거나 데이터가 복구되기 전에 컴포넌트가 마운트 해제되면 가져오기가 호출되지 않습니다.)
- This hook also takes the request config as a second parameter in order to be able to pass the authorization token in the header of the request,
for example. Be careful though, the latter does not trigger a re-rendering in case of modification, go through the url params to dynamically change the request.
(이 훅은 또한 요청의 헤더에 인증 토큰을 전달할 수 있도록 요청 구성을 두 번째 매개변수로 사용합니다(예: 요청 헤더에 인증 토큰 전달). 하지만 후자는 요청을 동적으로 변경하기 위해 URL 매개변수를 통해 요청을 수정하는 경우 재렌더링을 트리거하지 않으므로 주의하세요.)

### [useInterval](https://usehooks-ts.com/react-hook/use-interval)

- Use setInterval in functional React component with the same API.
  (동일한 API를 가진 함수형 React 컴포넌트에서 setInterval 사용.)
- Set your callback function as a first parameter and a delay (in milliseconds) for the second argument.
  (콜백 함수를 첫 번째 매개변수로 설정하고 두 번째 인수의 지연 시간(밀리초)을 설정합니다.)
- You can also stop the timer passing null instead the delay or even, execute it right away passing 0.
  (지연 대신 0을 전달하는 타이머를 중지하거나 0을 전달하는 타이머를 바로 실행할 수도 있습니다.)
- The main difference between the setInterval you know and this useInterval hook is that its arguments are "dynamic".
  (여러분이 알고 있는 setInterval과 이 useInterval 훅의 주요 차이점은 그 인수가 "동적"이라는 것입니다.)
- You can get more information in the Dan Abramov's [blog post](https://overreacted.io/making-setinterval-declarative-with-react-hooks/).
  (댄 아브라모프의 블로그 게시물에서 자세한 정보를 확인할 수 있습니다.)

### [useEventListener](https://usehooks-ts.com/react-hook/use-event-listener)

- Use EventListener with simplicity by React Hook.
  (이벤트 리스너를 React Hook으로 간단하게 사용하세요.)
- Supports Window, Element and Document and custom events with almost the same parameters as the native [addEventListener options](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#syntax).
  (기본 추가 이벤트 리스너 옵션과 거의 동일한 매개변수로 창, 요소, 문서 및 사용자 지정 이벤트를 지원합니다.)

### [useLocalStorage](https://usehooks-ts.com/react-hook/use-local-storage)

- Persist the state with local storage so that it remains after a page refresh.
  (페이지 새로 고침 후에도 상태가 유지되도록 로컬 저장소로 상태를 유지합니다.)
- This can be useful for a dark theme. This hook is used in the same way as useState except that you must pass the storage key in the 1st parameter.
  (어두운 테마에 유용할 수 있습니다. 이 훅은 첫 번째 매개변수에 저장소 키를 전달해야 한다는 점을 제외하면 useState와 동일한 방식으로 사용됩니다.)
- If the window object is not present (as in SSR), useLocalStorage() will return the default value.
  (window 객체가 없는 경우(SSR에서와 같이) useLocalStorage()는 기본값을 반환합니다.)

### [useDarkMode](https://usehooks-ts.com/react-hook/use-dark-mode)

- This React Hook offers you an interface to enable, disable, toggle and read the dark theme mode.
  (이 React Hook은 어두운 테마 모드를 활성화, 비활성화, 토글 및 읽을 수 있는 인터페이스를 제공합니다.)
- The returned value (isDarkMode) is a boolean to let you be able to use with your logic.
  (반환되는 값(isDarkMode)은 로직에 사용할 수 있도록 부울입니다.)
- It uses internally useLocalStorage() to persist the value and listens the OS color scheme preferences.
  (내부적으로 useLocalStorage()를 사용하여 값을 유지하고 OS 색 구성표 기본 설정을 수신합니다.)

## [SWR](https://swr.vercel.app/ko)

SWR은 데이터 가져오기, 캐싱 및 재검증을 위한 React 후크 라이브러리다.
이름은 HTTP RFC 5861에 의해 알려진 HTTP 캐시 무효 전략인 "stale-while-revalidate"에서 유래되었다.
SWR을 사용하면 API, 데이터베이스 또는 기타 소스에서 데이터를 가져온 다음 React 구성 요소의 데이터를 실시간으로 자동 업데이트할 수 있다.

SWR은 데이터를 메모리에 저장하고 사용 가능할 때 구성 요소에 즉시 반환하는 캐싱 메커니즘을 구현하여 이를 달성한다.
데이터가 오래된 경우(즉, 오래된 경우) SWR은 서버에서 새 데이터를 가져온 다음 백그라운드에서 캐시된 데이터를 업데이트한다.
이렇게 하면 UI가 최신 데이터로 반응하고 최신 상태를 유지한다.

SWR은 REST API, GraphQL 엔드포인트, 심지어 웹 소켓을 포함한 광범위한 데이터 소스를 지원한다.
또한 자동 유효성 재검사, 폴링 및 오류 처리와 같은 몇 가지 고급 기능을 제공한다. SWR의 주요 기능 중 일부는 다음과 같다.

1. 자동 캐싱: SWR은 데이터를 메모리에 자동으로 캐싱하고 사용 가능한 경우 구성 요소로 반환한다.
이렇게 하면 API 호출 수가 줄어들고 애플리케이션의 성능이 향상된다.
2. Stale-while-revalidate: 데이터가 오래되면 SWR은 백그라운드에서 서버에서 새 데이터를 가져오고 새 데이터를 사용할 수 있을 때 캐시된 데이터를 업데이트한다.
이렇게 하면 UI가 최신 데이터로 응답하고 최신 상태를 유지할 수 있다.
3. 실시간 업데이트: SWR은 웹 소켓과 같이 실시간 데이터를 제공하는 데이터 소스에 대한 실시간 업데이트를 지원한다.
4. 유연한 구성: SWR은 특정 사용 사례에 맞게 캐싱 및 재검증 동작을 사용자 정의할 수 있는 유연한 구성 API를 제공한다.

```js
import useSWR from 'swr'

function Profile() {
  const { data, error, isLoading } = useSWR('/api/user', fetcher)

  if (error) return <div>failed to load</div>
  if (isLoading) return <div>loading...</div>
  return <div>hello {data.name}!</div>
}
```

## [react-query](https://tanstack.com/query/latest)

React Query는 애플리케이션에서 서버 상태를 관리, 캐싱 및 업데이트하기 위한 React 라이브러리다.
API 및 기타 소스에서 데이터를 가져오고, 캐싱하고, 업데이트하는 프로세스를 간소화한다.
React Query는 선언적이고 효율적인 방식으로 비동기 데이터 가져오기 및 상태 관리를 처리할 수 있는 일련의 후크를 제공한다.

React Query는 자동 캐싱, 백그라운드 다시 가져오기, 스마트 데이터 동기화와 같은 기능을 도입하여 데이터 가져오기를 보다 효율적으로 처리하는 방법을 제공하는 것을 목표로 한다.
또한 네트워크 오류를 처리하고 데이터 가져오기가 항상 성공하도록 하는 데 사용할 수 있는 재시도 메커니즘이 내장되어 있다.

React Query의 주요 기능 중 일부는 다음과 같다.

1. 캐싱: React Query는 기본적으로 데이터를 캐싱하여 네트워크 요청 수를 줄이고 애플리케이션의 성능을 향상시킨다.
2. 자동 다시 가져오기: React Query는 UI가 항상 최신 데이터를 반영하도록 백그라운드에서 데이터를 자동으로 다시 가져온다.
3. 스마트 데이터 동기화: React Query는 이를 사용하는 모든 구성 요소에서 데이터가 동기화되도록 하므로 수동 데이터 동기화가 필요하지 않다.
4. 로딩 및 오류 상태: React Query는 데이터를 가져오는 동안 사용자에게 피드백을 제공하는 데 사용할 수 있는 내장 로딩 및 오류 상태를 제공한다.
5. 병렬 쿼리: React Query를 사용하면 데이터를 병렬로 가져올 수 있으므로 데이터를 가져오는 데 걸리는 시간이 줄어들어 애플리케이션의 성능이 향상된다.

```js
import {
  QueryClient,
  QueryClientProvider,
  useQuery,
} from '@tanstack/react-query'

const queryClient = new QueryClient()

export default function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <Example />
    </QueryClientProvider>
  )
}

function Example() {
  const { isLoading, error, data } = useQuery({
    queryKey: ['repoData'],
    queryFn: () =>
      fetch('https://api.github.com/repos/tannerlinsley/react-query').then(
        (res) => res.json(),
      ),
  })

  if (isLoading) return 'Loading...'

  if (error) return 'An error has occurred: ' + error.message

  return (
    <div>
      <h1>{data.name}</h1>
      <p>{data.description}</p>
      <strong>👀 {data.subscribers_count}</strong>{' '}
      <strong>✨ {data.stargazers_count}</strong>{' '}
      <strong>🍴 {data.forks_count}</strong>
    </div>
  )
}
```
