# 개발 환경

## Node.js

1995년 이후 JavaScript가 탄생하면서 많은 브라우저들이 JavaScript Engine을 탑재하기 시작했다.

- Safari(JavaScriptCore)
- Firefox(SpiderMonkey)
- IE(Chakara)
- Edge(Chakara -> V8)
- Chrome(V8)

2009년 Ryan Dahl이 Node.js를 개발하여 JavaScript로
브라우저 밖에서 서버를 구축하는 등의 코드를 실행할 수 있게 해주는 런타임 환경이다.

- Node.js가 설치된 환경에서는 아래와 같은 작업이 가능하다
  - Backend & Server
  - Front-end
  - Scripting & Automation

## NPM(Node Package Manager)

- Node.js의 패키지를 관리할 수 있는 도구 이다
- 현재 나는 npm대신 yarn을 사용하고 있다.

## yarn

- npm 패키지 관리자의 대안
- npm의 알려진 단점으로는 패키지 종속성 해결이 쉬운 만큼, 패키지가 중복 설치된다는 문제가 있다.
- yarn은 이 문제를 해결하기 위해 중복 패키지 발견 시 링크(바로가기) 방식으로 해결한다.

  > Yarn은 로컬 캐시로부터 패키지를 설치할 수 있다.
  > Yarn은 패키지 버전을 강력하게 바인딩한다.
  > Yarn은 데이터 무결성 보장을 위해 체크섬을 사용하는 반면 npm은 SHA-512를 사용하여 다운로드된 패키지의 데이터 무결성을 검사한다.
  > Yarn은 병렬로 패키지를 설치하는 반면 npm은 한 번에 하나의 패키지를 설치한다
  [wiki-Yarn](https://ko.wikipedia.org/wiki/Yarn_(%ED%8C%A8%ED%82%A4%EC%A7%80_%EA%B4%80%EB%A6%AC%EC%9E%90))

## package.json

```shell
  npm init -y
```

터미널에서 위의 명령어로 실행하면 기본적으로 아래와 같은 `package.json` 이 생성된다.

```json
{
  "name": "frontend-survival-week01",
  "version": "1.0.0",
  "description": "프론트엔드 생존코스 1주차 과제",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

패키지를 게시할 계획이라면 `name`과 `version`이 제일 중요한 항목이다.
그렇지 않다면 `name`과 `version`은 선택사항이다.

기본적인 package.json 설명은 [npm-package.json](https://docs.npmjs.com/cli/v7/configuring-npm/package-json#name)에서 참고하면 된다.

참고로 기억해둬야 할 부분

```shell
npm i <설치 할 모듈>
```

위와 같이 모듈를 설치하면 `package.json`에 dependencies 항목이 추가된다.

- dependencies: 프로그램에서 직접적으로 사용하는 모듈

```shell
npm i -D <설치 할 모듈> or npm install --save-dev <설치 할 모듈>
```

- devDependencies: 프로그램에서 사용하지는 않고 개발 환경에서 사용하는 모듈

## package-lock.json

- npm이 node_modules 트리 또는 package.json을 수정하는 모든 작업에 대해 자동으로 생성됩니다.

## node_modules

모듈 설치 시 프로젝트가 의존하고 있는 모듈 및 설치된 모듈이 의존하고 있는 모듈이 전부 가지고 있는 폴더

디렉터리가 없는 경우 외부 패키지를 다운로드 하면서 자동으로 생성됩니다.

## npx

npx는 새로운 패키지 관리 모듈이 아닙니다.

자바스크립트 패키지 관리 모듈인 npm(Node Package Module)의 5.2.0 버전부터 새로 추가된 도구입니다.

따라서 npm과 비교대상이 아닌 npm을 좀 더 편하게 사용하기 위해서 npm에서 제공해주는 하나의 도구입니다.

따라서 npm@5.2.0 이상 버전만 깔려 있다면 npx 명령어를 사용할 수 있습니다.

## Aha Moment

현재 실무에서 작업을 하면서 dependencies 또는 devDependencies 모듈을 추가 할 때
어떤 것은 dependencies에 들어가고
어떤 것은 devDependencies에 들어가는지 깊게 생각해 본적이 없었던 것 같다.
devDependencies에 들어가는건 대충 개발용이겠거니 생각했던 것 같다.

CRA를 통한 개발환경 자동 구축이 아닌 스탭 바이 스탭으로 하나씩 구축해가면서
프론트 개발환경에 필요한 설정을 직접 설정해보고 급격하게 변하는 상황에서
유연하게 적용 할 수 있도록 해야 겠다고 생각했다!
