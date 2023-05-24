# 3.Router

`<Router>`는 모든 라우터 컴포넌트(예: `<BrowserRouter>` 및 `<StaticRouter>`)가 공유하는 로우레벨 인터페이스다.
React의 관점에서 `<Router>`는 앱의 나머지 부분에 라우팅 정보를 제공하는 컨텍스트 프로바이더(Context Provider)다.

아마 `<Router>`를 수동으로 렌더링할 필요는 없을 것이다. 대신 환경에 따라 상위 레벨 라우터 중 하나를 사용해야 한다. 특정 앱에는 라우터가 하나만 필요하다.

`<Router basename>` 프로퍼티를 사용하면 앱의 모든 경로와 링크가 모두 공유하는 URL 경로명의 "basename" 부분에 상대적인 경로와 링크를 만들 수 있다.
이는 React 라우터로 더 큰 앱의 일부만 렌더링하거나 앱에 여러 진입점이 있는 경우에 유용하다. "basename"은 대소문자를 구분하지 않다.

## ReactRouter - RouterProvider

RouterProvider는 React Router v6에서 제공하는 컴포넌트 중 하나이다. 이 컴포넌트는 모든 데이터 라우터 객체를 이용해 앱을 렌더링하고 나머지 데이터 API를 활성화한다.

RouterProvider를 사용하고 싶다면, 다음과 같이 import하고 사용할 수 있다

```js
import { createBrowserRouter, RouterProvider } from "react-router-dom";

const router = createBrowserRouter([
  {
    path: "/",
    element: <Root />,
    children: [
      { path: "dashboard", element: <Dashboard /> },
      { path: "about", element: <About /> },
    ],
  },
]);

ReactDOM.createRoot(document.getElementById("root")).render(
  <RouterProvider router={router} fallbackElement={<BigSpinner />} />
);
```
