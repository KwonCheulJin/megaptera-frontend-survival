# 2.Fetch API & CORS

## Fetch API 란

Fetch API는 서버에서 리소스를 가져오기 위한 최신 JavaScript 인터페이스다.
이전 XMLHttpRequest(XHR) API보다 HTTP 요청을 만들고 응답을 처리하는 더 간단하고 유연하며 강력한 방법을 제공한다.

Fetch API는 URL을 가져와 요청에 대한 서버의 응답을 나타내는 Response 객체로 확인되는 Promise를 반환하는 fetch() 메서드를 제공한다.
Response 개체는 응답 헤더, 본문 및 상태를 검사하는 메서드를 제공한다.
Response 개체를 사용하여 Blob 및 JSON 개체와 같은 다른 유용한 개체를 만들 수도 있다.

```js
fetch('https://example.com/data.json')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

이 예제에서는 fetch() 메서드를 사용하여 URL 'https://example.com/data.json'에서 JSON 파일을 가져옵니다.
그런 다음 fetch()에 의해 반환된 Promise는 응답 객체의 json() 메서드를 호출하도록 연결되어 응답 본문을 JSON으로 구문 분석하고 다른 Promise를 반환한다.
마지막 then() 메서드는 JSON 데이터를 콘솔에 기록하는 데 사용되며 catch() 메서드는 가져오기 작업 중에 발생할 수 있는 모든 오류를 처리한다.

Fetch API는 헤더, 메서드 및 본문과 같은 요청을 사용자 지정하는 옵션도 제공한다.

```js
fetch('https://example.com/api/data', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({ key1: 'value1', key2: 'value2' })
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

이 예제에서는 JSON 페이로드와 함께 URL 'https://example.com/api/data'에 POST 요청을 보내는 데 fetch() 메서드가 사용된다.
headers 옵션은 페이로드의 콘텐츠 유형을 지정하는 데 사용되고 body 옵션은 JSON 데이터를 문자열로 제공하는 데 사용된다.
그런 다음 서버는 요청 본문에서 JSON 데이터를 구문 분석할 수 있다.

전반적으로 Fetch API는 최신 웹 애플리케이션에서 HTTP 요청을 만들기 위한 강력하고 유연한 도구이다.
요청을 만들고 응답을 처리하는 프로세스를 단순화하고 사용하고 이해하기 쉬운 깔끔한 Promise 기반 API를 제공한다.

### Blob

Blob(Binary Large Object)은 이미지, 오디오 또는 비디오 파일과 같은 이진 데이터 청크를 나타내는 JavaScript의 데이터 유형이다.
Blob은 서버에서 보내거나 서버에서 받아야 하는 이진 데이터로 작업할 때 웹 개발에 유용하다.

Blob 개체는 실제 이진 데이터와 데이터를 설명하는 메타데이터 집합(예: MIME 유형 및 파일 이름)의 두 부분으로 구성된다.
이진 데이터는 텍스트, 이미지, 오디오 또는 비디오를 포함한 모든 유형의 데이터가 될 수 있다.

웹 개발에서 Blob의 일반적인 용도 중 하나는 사용자가 파일을 서버에 업로드할 수 있도록 하는 것이다.
Blob API는 파일 입력 요소에서 새 Blob 개체를 만드는 방법을 제공하며, 그런 다음 Fetch API 또는 XHR을 사용하여 서버로 보낼 수 있다.

## Promise

JavaScript에서 Promise는 아직 사용할 수 없지만 미래의 어느 시점에 있을 값을 나타내는 내장 개체다.
Promise는 비동기 코드를 작성하고 서버에서 데이터를 가져오거나 사용자 입력을 처리하는 것과 같은 비동기 작업을 처리하는 프로세스를 단순화하므로 현대 웹 개발의 기본 도구다.

Promise 객체에는 보류, 이행 및 거부의 세 가지 상태가 있다.
Promise가 생성되면 대기 중 상태가 된다.
이는 Promise가 나타내는 값을 아직 사용할 수 없음을 의미한다.
Promise가 이행되면 이행 상태가 되고 Promise가 나타내는 값을 사용할 수 있다.
실행 중에 Promise에 오류가 발생하면 Promise는 거부된 상태가 되고 오류 개체가 반환된다.

Promise을 만들기 위한 기본 구문은 다음과 같다.

```js
const promise = new Promise((resolve, reject) => {
  // 비동기 코드 작성
  if (/* 비동기 작업 성공 */) {
    resolve(/* 반환할 값 */);
  } else {
    reject(/* 에러 */);
  }
});
```

이 예에서는 resolve 및 reject라는 두 개의 매개변수를 사용하는 함수를 사용하여 새 Promise를 만듭니다.
함수에는 결국 Promise를 해결하거나 거부할 비동기 코드가 포함되어 있다.
작업이 성공하면 반환할 값과 함께 resolve 함수가 호출된다. 실패하면 오류 개체와 함께 거부 함수가 호출된다.

Promise를 사용하려면 then() 메서드를 호출하여 이행된 상태를 처리하거나 catch() 메서드를 호출하여 거부된 상태를 처리할 수 있다.

```js
promise
  .then(value => {
    // 완료 상태 처리
  })
  .catch(error => {
    // 거부된 상태 처리
  });
```

이 예에서 then() 메서드는 Promise의 이행 상태를 처리하는 데 사용되고 catch() 메서드는 거부된 상태를 처리하는 데 사용된다.
이러한 메서드에 전달된 콜백 함수는 각각 Promise에서 반환된 값 또는 오류 개체를 받다.

Promise는 then() 메서드를 사용하여 연결될 수도 있으므로 보다 복잡한 작업을 순차적으로 수행할 수 있다.
예를 들어 다른 Promise가 이행된 후 Promise를 실행해야 하는 경우 두 Promise를 함께 연결할 수 있다.

```js
const promise1 = new Promise((resolve, reject) => {
  // Asynchronous code here
});

const promise2 = promise1.then(value => {
  // Handle fulfilled state of promise1
  return /* value or new Promise */;
});

promise2
  .then(value => {
    // Handle fulfilled state of promise2
  })
  .catch(error => {
    // Handle rejected state of either promise1 or promise2
  });
```

이 예에서 promise2는 then() 메서드를 사용하여 promise1에 연결되어 promise1이 이행된 후 실행될 수 있다.
then()에 전달된 콜백 함수는 체인의 다음 then() 메서드에 전달되는 새 값 또는 Promise를 반환한다.

전반적으로 Promise는 JavaScript에서 비동기 코드를 처리하기 위한 강력한 도구다.
비동기 작업 작업을 위한 깨끗하고 이해하기 쉬운 인터페이스를 제공하고 일관된 방식으로 성공 및 오류 사례를 간단하게 처리할 수 있도록 한다.

## ReadableStream

ReadableStream은 최신 웹 브라우저와 Node.js에 내장된 객체로, 데이터 소스에서 소비자로 데이터, 특히 대용량 데이터세트를 효율적으로 스트리밍할 수 있다.
ReadableStream은 제어되고 효율적인 방식으로 데이터 스트림을 비동기식으로 생성하는 메커니즘을 제공하여 소비자가 전체 데이터 세트가 메모리에 로드될 때까지 기다리지 않고 데이터가 도착하는 대로 데이터를 처리할 수 있도록 한다.

ReadableStream은 데이터를 생성하는 소스와 데이터를 수신하고 처리하는 소비자로 구성된다.
소스는 파일, 네트워크 연결 또는 생성된 데이터 스트림과 같은 모든 유형의 데이터가 될 수 있다.
소비자는 데이터를 파일에 쓰거나 알고리즘으로 처리하거나 UI에 표시하는 것과 같은 모든 유형의 작업이 될 수 있다.

ReadableStream을 생성하기 위한 기본 구문은 다음과 같다.

```js
const stream = new ReadableStream({
  start(controller) {
    // 비동기 데이터 생성 코드 작성
  },
  cancel() {
    // 선택적으로 정리 코드 작성
  }
});
```

이 예제에서는 start() 및 cancel()이라는 두 가지 메서드가 포함된 개체를 사용하여 새 ReadableStream을 만든다.
start() 메서드에는 데이터를 비동기적으로 생성하는 코드가 포함되어 있으며 스트림 제어를 위한 메서드를 제공하는 컨트롤러 개체가 전달된다.
cancel() 메서드는 선택 사항이며 소비자가 스트림을 취소한 경우 실행되는 정리 코드를 포함한다.

ReadableStream에서 데이터를 사용하려면 판독기 개체를 만들고 해당 read() 메서드를 사용하여 사용 가능한 데이터 청크를 검색할 수 있다.

```js
const reader = stream.getReader();

function readData() {
  reader.read().then(({ done, value }) => {
    if (done) {
      console.log('End of stream');
      return;
    }

    console.log(`Data chunk: ${value}`);
    readData();
  });
}

readData();
```

이 예제에서는 ReadableStream 개체의 getReader() 메서드를 사용하여 판독기 개체를 만든다.
그런 다음 readData() 함수는 read() 메서드에서 반환된 Promise를 사용하여 재귀적으로 호출된다.
이 메서드는 스트림이 종료되었는지 여부를 나타내는 부울 값과 데이터 덩어리를 포함하는 객체로 확인된다.

전반적으로 ReadableStreams는 웹 개발에서 효율적인 데이터 스트리밍을 위한 강력한 도구다.
스트리밍 데이터를 위한 표준화된 인터페이스를 제공하여 특히 대규모 데이터 세트로 작업할 때 효율적인 데이터 스트리밍 코드를 구현하고 유지 관리하기가 더 쉽다.

## Unicode

Unicode는 전 세계 언어의 스크립트를 포함하여 인간 언어에서 사용되는 각 문자에 고유한 숫자 값(코드 포인트)을 할당하는 범용 문자 인코딩 표준이다.
Unicode의 목표는 정보 손실 없이 다양한 플랫폼, 응용 프로그램 및 장치 간에 텍스트 데이터를 교환할 수 있도록 모든 언어 또는 스크립트로 텍스트를 나타내는 일관된 방법을 제공하는 것이다.

Unicode는 문자, 숫자, 문장 부호, 기호 및 제어 문자를 포함하여 143,000개 이상의 문자를 포함하는 크고 복잡한 표준이다.
각 문자는 0x000000에서 0x10FFFF까지의 32비트 정수인 고유한 코드 포인트로 식별된다.

Unicode 표준은 UTF-8, UTF-16 및 UTF-32를 포함하여 Unicode 문자를 이진 형식으로 나타내는 여러 인코딩 체계를 정의한다.
각 인코딩 체계는 Unicode 코드 포인트를 컴퓨터에서 저장, 전송 및 처리할 수 있는 일련의 바이트에 매핑한다.

UTF-8은 가장 널리 사용되는 인코딩 체계이며 영어의 원래 7비트 문자 인코딩 표준인 ASCII와의 하위 호환성을 제공한다.
UTF-8은 단일 바이트로 인코딩된 ASCII 문자를 사용하여 코드 포인트의 값에 따라 각 Unicode 코드 포인트를 1~4바이트로 인코딩한다.
UTF-16은 각 Unicode 코드 포인트를 하나 또는 두 개의 16비트 코드 단위로 인코딩하고 UTF-32는 각 코드 포인트를 단일 32비트 코드 단위로 인코딩한다.

Unicode는 현대 컴퓨팅의 필수 요소가 되었으며 소프트웨어 개발, 웹 응용 프로그램, 데이터베이스 관리 및 운영 체제에서 광범위하게 사용된다.
이를 통해 개발자는 모든 언어 또는 스크립트의 텍스트 데이터를 처리할 수 있는 다국어 응용 프로그램을 만들 수 있으므로 서로 다른 문화 및 지역 간에 더 쉽게 통신할 수 있다.

요약하면 Unicode는 각 문자에 할당된 고유한 코드 포인트를 사용하여 모든 언어 또는 스크립트로 텍스트 데이터를 나타내는 표준화된 방법이다.
UTF-8, UTF-16 및 UTF-32와 같은 Unicode 인코딩 체계는 컴퓨터에서 저장, 전송 및 처리할 수 있는 Unicode 문자의 이진 표현을 제공한다.

## CORS 란

CORS는 Cross-Origin Resource Sharing의 약자로, 웹 페이지가 제공된 도메인이나 포트가 아닌 다른 도메인이나 포트에 대한 요청을 하지 못하도록 웹 페이지를 제한하는 최신 웹 브라우저에 구현된 보안 기능이다.
CORS는 악의적인 스크립트가 여러 도메인에서 중요한 데이터에 액세스하지 못하도록 방지하는 데 도움이 되는 필수 보안 기능이다.

동일 출처 정책(same-origin policy)은 웹 페이지가 자체 출처가 아닌 다른 출처(도메인, 프로토콜 또는 포트)의 리소스에 액세스하는 것을 제한하는 웹 브라우저에 의해 구현된 기본 보안 개념이다.
그러나 웹 페이지가 다른 도메인에서 호스팅되는 REST API와 같이 다른 출처의 리소스에 액세스해야 하는 유효한 사용 사례가 있다.
CORS는 제어된 방식으로 동일한 출처 정책을 완화하는 메커니즘을 제공하여 웹 페이지가 출처 간 요청을 할 수 있도록 하는 동시에 악의적인 스크립트가 기능을 남용하지 못하도록 한다.

CORS는 서버의 응답에 HTTP 헤더를 추가하여 작동하며, 이는 원본 간 요청을 할 수 있는 도메인과 지원되는 HTTP 메서드를 나타낸다.
서버는 다음 CORS 헤더 중 하나로 응답할 수 있다.

- Access-Control-Allow-Origin: 리소스에 액세스할 수 있는 도메인을 지정한다. 헤더가 없거나 와일드카드 "*"가 포함된 경우 모든 도메인이 리소스에 액세스할 수 있다.
- Access-Control-Allow-Methods: GET, POST, PUT, DELETE 등과 같은 원본 간 요청에 대해 허용되는 HTTP 메서드를 지정한다.
- Access-Control-Allow-Headers: 교차 출처 요청에 허용되는 요청 헤더를 지정한다.
- Access-Control-Allow-Credentials: 원본 간 요청에 쿠키 또는 HTTP 인증과 같은 자격 증명을 포함할 수 있는지 여부를 나타낸다.

웹 페이지가 교차 출처 요청을 하면 웹 브라우저는 요청된 리소스가 허용되는지 확인하기 위해 프리플라이트 요청을 서버로 보낸다.
실행 전 요청에는 HTTP OPTIONS 메서드와 원본 간 요청 세부 정보를 지정하는 추가 헤더가 포함된다.
서버는 원본 간 요청이 허용되는지 여부를 나타내는 적절한 CORS 헤더로 응답한다.
요청이 허용되면 웹 브라우저는 요청된 메서드 및 헤더와 함께 실제 요청을 보낸다.
preflight 요청은 cross-origin 요청이 허용되는지 확인하는 데 사용되며 서버는 적절한 CORS 헤더로 응답한다.

## Reference

- [ReadableStream](https://developer.mozilla.org/ko/docs/Web/API/ReadableStream)
