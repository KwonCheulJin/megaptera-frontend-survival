# 1.Express

## Express 란

1. Node.js를 기반으로 구축되었다. 즉, Node.js와 동일한 비동기 이벤트 기반 프로그래밍 모델을 사용한다. 따라서 확장 가능한 고성능 웹 애플리케이션을 구축하는 데 이상적이다.
2. 로깅, 오류 처리, 인증 등과 같은 기능을 애플리케이션에 추가하는 데 사용할 수 있는 광범위한 미들웨어 모듈을 제공한다. 또한 고유한 미들웨어 함수를 작성하여 애플리케이션의 동작을 사용자 정의할 수 있다.
3. 동적 HTML 페이지를 생성하는 데 사용할 수 있는 Pug(이전의 Jade), EJS 및 Handlebars를 비롯한 다양한 템플릿 엔진을 지원한다.
4. 애플리케이션에 대한 URL 경로를 정의하고 이를 특정 작업 또는 핸들러에 매핑할 수 있는 강력한 라우팅 시스템을 제공한다. 이를 통해 RESTful API를 쉽게 생성하고 복잡한 HTTP 요청을 처리할 수 있다.
5. 크고 활발한 개발자 커뮤니티가 있다. 즉, 기능을 확장하는 데 사용할 수 있는 많은 타사 모듈과 플러그인이 있다. npm(Node.js 패키지 관리자)을 사용하여 쉽게 설치할 수 있다.

## URL 구조

- URL(Uniform Resource Locator)은 인터넷에서 리소스를 식별하는 데 사용되는 문자열이다.

`protocol://domain_name_or_IP_address:port/path?query_string#fragment_identifier`

1. 프로토콜(Protocol): 프로토콜은 HTTP, HTTPS, FTP 또는 SSH와 같이 데이터를 전송하는 데 사용되는 프로토콜(컴퓨터 내부에서, 또는 컴퓨터 사이에서 데이터의 교환 방식을 정의하는 규칙 체계)을 지정한다.

2. 도메인 이름 또는 IP 주소(Domain Name or IP Address): 도메인 이름 또는 IP 주소는 리소스를 호스팅하는 서버를 식별한다.
도메인 이름은 DNS(도메인 이름 시스템)에 의해 IP 주소로 변환되는 사람이 읽을 수 있는 이름이다. 예를 들어 'www.google.com'은 IP 주소 '216.58.194.174'에 해당하는 도메인 이름이다.

3. 포트(Port): 포트 번호는 요청을 수신하기 위해 서버에서 사용하는 네트워크 포트를 식별한다. 포트를 지정하지 않으면 프로토콜의 기본 포트가 사용된다(예: HTTP의 경우 포트 80).

4. 경로(Path): 경로는 서버에서 리소스의 위치를 ​​지정한다. 일반적으로 슬래시로 구분된 일련의 디렉터리 및 파일 이름으로 구성된다.
예를 들어 URL <http://www.example.com/images/logo.png에서> 경로는 /images/logo.png이다.

5. 쿼리 문자열(Query String): 쿼리 문자열은 검색 매개변수 또는 양식 데이터와 같은 리소스에 대한 추가 정보를 제공한다.
물음표로 시작하고 앰퍼샌드로 구분된 일련의 키-값 쌍으로 구성된다.
예를 들어 URL <http://www.example.com/search?q=example&limit=10에서> 쿼리 문자열에는 q=example 및 limit=10이라는 두 개의 키-값 쌍이 포함되어 있다.

6. 조각 식별자(Fragment Identifier): 조각 식별자는 HTML 문서 내의 섹션과 같은 리소스의 특정 부분을 식별한다.
해시 기호(#)로 시작하고 문자열로 구성된다.
예를 들어 URL <http://www.example.com/page.html#section2에서> 프래그먼트 식별자는 section2이다.

`URL 구조는 인터넷에서 리소스를 찾고 액세스하는 표준화된 방법을 제공하여 사용자가 웹을 쉽게 탐색하고 필요한 정보에 액세스할 수 있도록 해준다`

## REST API

REST API는 Representational State Transfer Application Programming Interface의 약자이다.

REST는 일련의 제약 조건을 기반으로 웹 서비스가 작동하는 방식을 정의하는 아키텍처 스타일이다.

REST는 처음에 인터넷과 같은 복잡한 네트워크에서 통신을 관리하기 위한 지침으로 만들어졌다.
인터넷을 통해 모든 장치 또는 플랫폼에서 액세스할 수 있는 가볍고 확장 가능하며 유지 관리 가능한 웹 서비스를 구축하는 데 사용된다.

API는 서로 다른 소프트웨어 응용 프로그램이 서로 통신할 수 있도록 하는 규칙 또는 프로토콜 집합이다.

REST 아키텍처 스타일을 따르는 API를 REST API라고 한다.

REST API에는 아키텍처를 정의하고 웹 기반 애플리케이션을 구축하는 데 널리 사용되는 몇 가지 특성이 있다. 주요 특징 중 일부는 다음과 같다.

1. 상태 비저장(Stateless): REST API는 상태 비저장이므로 요청 간에 클라이언트 컨텍스트를 저장하지 않는다.
  클라이언트의 각 요청에는 서버가 요청을 처리하는 데 필요한 모든 정보가 포함되어 있다.

2. 클라이언트-서버 아키텍처(Client-server architecture): REST API는 클라이언트와 서버가 서로 분리되고 독립적인 클라이언트-서버 아키텍처를 따른다.
  클라이언트는 서버에 요청(request)을 보내고 서버는 응답(response)을 다시 보낸다.

3. 통일된 인터페이스(Uniform interface): REST API에는 통일된 인터페이스가 있다.
  즉, GET, POST, PUT, DELETE 등과 같은 표준 HTTP 메서드 집합을 사용하여 리소스와 상호 작용한다. 이를 통해 개발자는 API를 더 쉽게 사용하고 이해할 수 있다.

4. 리소스 기반(Resource-based): REST API는 리소스 기반이다.
  즉, API의 모든 구성 요소는 고유한 URI(Uniform Resource Identifier)로 식별된다. 이러한 리소스는 파일, 데이터베이스 또는 기타 유형의 데이터일 수 있다.
  데이터는 일반적으로 다양한 플랫폼에서 쉽게 이해할 수 있는 범용 데이터 형식인 JSON 또는 XML 형식이다.

5. 캐시 가능: REST API는 캐시 가능하도록 설계되었다. 즉, 서버의 응답을 클라이언트가 캐시하여 성능을 향상시킬 수 있다.

6. 계층화된 시스템: REST API는 계층화된 시스템으로 설계되었다.
  즉, 클라이언트는 서버의 기본 구현에 대해 알 필요가 없다. 이렇게 하면 클라이언트에 영향을 주지 않고 서버를 쉽게 업데이트하거나 수정할 수 있다.

전반적으로 REST API는 단순하고 확장 가능하며 유연하도록 설계되어 웹 기반 애플리케이션 구축에 널리 사용된다.

## HTTP Method(CRUD)

HTTP(Hypertext Transfer Protocol)는 웹 서버와 클라이언트 간의 통신에 사용되는 프로토콜이다.
HTTP는 리소스에서 수행할 원하는 작업을 나타내는 요청 메서드(또는 동사) 집합을 정의한다.
HTTP 메서드는 URL로 식별되는 리소스에서 수행할 작업을 지정한다.

1. GET: GET 방식은 서버에서 리소스를 검색하는 데 사용된다.
이것은 안전하고 멱등적인(idempotent) 방법이다.
즉, 여러 개의 동일한 요청이 동일한 응답을 생성한다는 의미이다.
GET 메서드는 서버의 리소스 상태를 변경하지 않다.

2. POST: POST 방식은 새로운 리소스를 생성하거나 기존 리소스를 업데이트하기 위해 서버에 데이터를 제출하는 데 사용된다.
이는 안전하거나 멱등성이 아니다.
즉, 여러 개의 동일한 요청이 다른 응답을 생성하거나 서버의 리소스 상태를 수정할 수 있다.

3. PUT: PUT 메서드는 서버의 기존 리소스를 업데이트하는 데 사용된다.
이는 멱등적(idempotent)이며 여러 개의 동일한 요청이 동일한 결과를 생성한다는 의미이며 안전하지 않아 서버의 리소스 상태를 수정할 수 있음을 의미한다.

4. DELETE: DELETE 메소드는 서버의 리소스를 삭제하는 데 사용된다.
멱등성(idempotent)은 여러 개의 동일한 요청이 동일한 결과를 생성함을 의미하며 안전하지 않아 서버의 리소스 상태를 수정함을 의미한다.

5. PATCH: PATCH 방식은 서버의 리소스 일부를 업데이트하는 데 사용된다.
이는 안전하거나 멱등성이 아니다.
즉, 여러 개의 동일한 요청이 다른 응답을 생성하거나 서버의 리소스 상태를 수정할 수 있다.

6. HEAD: HEAD 메소드는 리소스 자체를 검색하지 않고 리소스에 대한 헤더 정보를 검색하는 데 사용된다.
안전하고 멱등적인(idempotent) 방법이다.

7. OPTIONS: OPTIONS 메서드는 지원되는 메서드 및 리소스에 대한 기타 정보를 검색하는 데 사용된다.
안전하고 멱등적인(idempotent) 방법이다.

### 멱등성(Idempotent)

동일한 요청을 한 번 보내는 것과 여러 번 연속으로 보내는 것이 같은 효과를 지니고, 서버의 상태도 동일하게 남을 때, 해당 HTTP 메서드가 멱등성을 가졌다고 말한다.

즉, `멱등성 연산은 한 번 또는 여러 번 수행해도 결과는 동일하다.`

예를 들어 두 개의 숫자를 더하는 계산기를 생각해 보자. 2 + 3을 한 번 더하면 결과는 5가 된다.
다시 2 + 3을 더해도 결과는 여전히 5다. 이 작업을 여러 번 수행해도 같은 결과가 나오므로 이 작업은 멱등적이다.

웹 개발의 맥락에서 멱등성은 서버에 대한 반복 요청이 단일 요청과 동일한 효과를 갖도록 보장하기 때문에 중요하다.
예를 들어 HTTP GET 메서드를 사용하여 서버에서 리소스를 검색하는 경우 리소스가 서버에서 수정되지 않기 때문에 멱등성 작업이다.
리소스 상태를 변경하지 않고 원하는 만큼 GET 요청을 반복할 수 있다.

반면에 HTTP POST 메서드는 양식을 여러 번 제출하면 서버에서 리소스를 만들거나 수정하라는 여러 요청이 발생하기 때문에 멱등성이 아니다.
이는 서버가 여러 요청을 처리하도록 설계되지 않은 경우 의도하지 않은 결과를 초래할 수 있다.

요약하면 멱등성을 통해 의도하지 않은 결과 없이 작업을 여러 번 수행할 수 있다.
서버가 예기치 않은 동작을 일으키지 않고 반복되는 요청을 처리할 수 있도록 보장하는 것은 웹 개발에서 중요한 개념이다.
