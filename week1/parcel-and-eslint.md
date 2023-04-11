# Parcel, ESLint

## Parcel

현재 나는 회사에서 프로젝트 구성으로 webpack을 사용하고 있는 중이다.
1주차 강의를 들으면서 이곳에서 parcel을 사용하기에 왜 parcel을 사용하는지 궁금하였다.
그래서 구글링을 통해서 검색한 블로그를 바탕으로 특징있는 부분만 요약하였다.

`Parcel`은 설정이 필요없는 zero-configuration 이기 때문에, 빌드를 위해 번들러를 학습하는 시간을 많이 줄일 수 있습니다.

`Webpack`에 비하면 이 부분은 큰 장점인 것 같다. `Webpack`을 사용하면서 일부 설정을 건드려야 하는
부분이 발생 했을 때 `Webpack` 공식문서가 잘 되어있지만 수정해야 하는 부분에 대한 설정 파악과 함께 써야
하는 `plugin` 종류도 많고 공식문서를 보고 작성했어도 내 이해의 한계로 인해서 잘 못 설정한 부분도 있었던 터라 `Parcel`의 설정이 필요없는 부분은 정말 매력적인 것 같다.

### Transformations

- `Parcel`은 zero-configuration 특징으로 별도의 설정파일 없이 다양한 변환을 지원합니다.

### Tree Shaking (Dead code elimination)

- `Parcel`은 ES6및 CommonJS 모듈 모두에 대해 Tree shaking을 지원합니다. 또한 대부분의 작업을 캐싱하여 다시 빌드할 경우 빠른 속도를 지니고 있습니다.

### Code splitting

- `Parcel`의 Code splitting은 zero-configuration 이라는 특징으로 확인 할 수 있습니다. import() 함수 구문 을 사용하여 제어되며, 이는 일반 import 문이나 require 함수처럼 작동하지만 Promise를 반환합니다. 이는 모듈이 비동기적으로 로드됨을 의미합니다.

### Dev Server

- `Parcel`은 Dev server가 내장되어 있고, 파일이 변경할 경우 다시 빌드 합니다.

### Hot Module Replacement

- `Parcel`은 기본적으로 HMR을 지원합니다.
- 이 기능은 코드가 실행되는 동안 전체 리로드를 할 필요없이 모듈을 추가, 제거 할 수 있는 기능을 이야기 합니다.

`Parcel`에서도 zero-configuration이라고 했지만 plugin을 제공해 소규모에서 대규모 애플리케이션까지 확장 가능하게 지원해주고 있다.

----

- 참고
- [Parcel vs Rollup vs Webpack 비교](https://velog.io/@subin1224/Parcel-vs-Rollup-vs-Webpack-%EB%B9%84%EA%B5%90)
- [Parcel 공식문서](https://parceljs.org/)

----

## ESLint

`ESLint`는 JavaScript, JSX의 정적 분석 도구로 오픈 소스 프로젝트입니다.
코드를 분석해 문법적인 오류나 안티 패턴을 찾아주고 일관된 코드 스타일로 작성하도록 도와줍니다.
JSLint, JSHint와 같이 다른 JavaScript 정적 분석 도구들도 있지만,
`ESLint`가 커스터마이징이 쉽고 확장성이 뛰어나 많이 쓰이고 있는 추세입니다.
`ESLint`는 스타일 가이드를 좀 더 편리하게 적용하기 위해 사용하기도 하는데,
외부에 공개되어 많은 개발자가 사용 중인 Airbnb Style Guide, Google Style Guide 가 그 대표적인 예입니다.

현재 서비스 중인 프로젝트에서도 `ESLint`를 사용하고 있지만 혼자 작업을 하다보니 `Coding convention`이 제대로 지켜지지 않을 때가 많았다.

`ESLint`가 있지만 내가 보기 편한 쪽으로 하기 위해서 린트를 꺼버리는 경우도 있었는데 앞으로는 특별한 경우가 아닌 이상 린트를 통해서 일관성 있는 코드를 작성하도록 노력해야겠다.

----

- 참고
- [ESLint 조금 더 잘 활용하기](https://tech.kakao.com/2019/12/05/make-better-use-of-eslint/)
- [ESLint 공식문서](https://eslint.org/)

----
