# 1.React Component

## REST API 와 GraphQL

### REST API 란 무엇인가

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

### GraphQL은 왜 등장했는가?

GraphQL은 오픈 소스 쿼리 언어이자 API용 런타임으로, 2012년 Facebook이 REST API에서 직면한 문제를 해결하기 위해 처음 개발했다.
REST API는 API를 구축하는 표준 방식이 되었지만, Facebook의 데이터가 점점 더 복잡해지면서 쿼리를 최적화하고 데이터를 과도하게 가져오거나 적게 가져오는 것을 방지하는 것이 어려워졌었다고 한다.

GraphQL은 클라이언트가 필요한 데이터만 요청할 수 있도록 함으로써 보다 효율적이고 유연한 데이터 쿼리 방법을 제공하기 위해 개발되었다.
클라이언트가 데이터 요구 사항을 지정하는 데 사용할 수 있는 강력하게 유형화된 스키마를 제공함으로써 이를 달성하고, 서버에서 이를 해결한다.

GraphQL의 주요 기능 중 하나는 서로 다른 리소스에 대한 여러 엔드포인트가 아닌 모든 데이터 쿼리에 대해 단일 엔드포인트를 제공할 수 있다는 점이다.
이렇게 하면 API가 단순화되고 빌드 및 유지 관리에 필요한 코드의 양이 줄어든다.

### REST API vs GraphQL

#### REST API

- 장점

1. 배우기 쉽고 업계에서 널리 채택되었다.
2. GET, POST, PUT, DELETE와 같은 다양한 HTTP 메서드 지원한다.
3. 캐싱 및 보안을 쉽게 구현할 수 있다
4. 상태 비저장성을 지원하여 확장이 용이하다.
5. 웹, 모바일, IoT 등 다양한 애플리케이션에 사용 가능하다.

- 단점

1. 데이터의 오버 페칭과 언더 페칭이 발생하여 네트워크 지연과 성능 저하를 초래할 수 있다.
2. 다양한 리소스에 대해 여러 엔드포인트가 필요하므로 코드 복잡성 및 유지 관리 문제 발생 할 수 있다.
3. 버전 관리가 제대로 지원되지 않아 새로운 기능이 추가될 때 변경 사항이 중단될 수 있다.
4. 매우 복잡하고 중첩된 데이터 구조에 적합하지 않다.

#### GraphQL

- 장점

1. 클라이언트가 필요한 데이터만 요청할 수 있어 네트워크 대기 시간을 줄이고 성능을 개선한다.
2. 강력하게 유형화된 스키마를 제공하므로 개발자가 API를 더 쉽게 이해하고 작업할 수 있다.
3. 모든 데이터 쿼리를 위한 단일 엔드포인트를 제공하여 API를 간소화하고 코드 복잡성을 줄인다.
4. 실시간 데이터 업데이트 및 구독 기능을 지원한다.
5. 매우 복잡하고 중첩된 데이터 구조 처리 가능하다.

- 단점

1. GraphQL에 익숙하지 않은 개발자에게는 학습 곡선 필요하다.
2. 캐싱과 보안을 구현하는 데 더 많은 노력이 필요하다.
3. REST API만큼 널리 채택되지 않아 리소스 및 도구를 찾기가 더 어려울 수 있다.
4. 데이터 검색의 유연성으로 인해 더 큰 페이로드가 발생하여 잠재적인 네트워크 정체를 초래할 수 있다.

요약하자면, REST API는 광범위한 애플리케이션을 지원하고 캐싱과 보안을 쉽게 구현할 수 있는 널리 채택된 표준이다.
하지만 데이터의 오버페칭 및 언더페칭으로 인해 네트워크 지연과 성능 저하가 발생할 수 있다.
반면 GraphQL은 데이터를 쿼리하는 보다 효율적이고 유연한 방법을 제공하지만, 캐싱 및 보안을 구현하는 데 학습 곡선과 더 많은 노력이 필요하다.
매우 복잡하고 중첩된 데이터 구조에 적합하며 모든 데이터 쿼리에 대해 단일 엔드포인트를 제공하므로 코드 복잡성이 줄어든다.

## Aha Moment

REST API를 사용하다 보면 종종 드는 생각이 화면을 구성하는데 필요한 정보보다 서버에서 보내주는 응답값이 과도하게 정보가 담겨있는 경우가 종종 발생한다.
화면 만을 위한 데이터로 구성이 되기보다 더 많은 정보를 담고 있는 경우도 있기 때문에 화면에서 사용하지 않는 데이터가 신경쓰이지만 달리 방법이 없다.
아마도 페이스북은 이런 경우에 이것들을 모두 컨트롤하는거에서 문제점을 발견하고 GraphQL을 개발했다고 생각이 든다.
내가 서비스를 구축하면서 사용 해본 적은 없고 대략적인 사용법 정도만 알고 있지만 GraphQL을 사용했을 때의 장점은 클라이언트에서 필요한 데이터만 가져가다 사용할 수 있다는 점을 알고 있다.
REST API와 GraphQL 둘 다 장단점이 명확해서 어느게 더 좋다라고 할 수는 없지만 어떤 서비스를 구축하느냐에 따라 어떤게 좋은지는 그때 갈릴 것 같다.

## JSON

JSON(JavaScript Object Notation)은 사람이 읽고 쓰기 쉽고 기계가 구문 분석하고 생성하기 쉬운 경량 데이터 교환 형식입니다.
모든 프로그래밍 언어와 함께 사용할 수 있는 언어 독립적인 데이터 형식으로 만들어졌다.

JSON 데이터는 키-값 쌍으로 구성되며 키는 항상 문자열이고 값은 문자열, 숫자, 부울, 객체 또는 배열과 같은 유효한 JSON 데이터 유형입니다.
객체는 중괄호로 묶인 키-값 쌍의 모음인 반면 배열은 대괄호로 묶인 정렬된 값 모음입니다.
JSON 데이터는 다른 개체 또는 배열을 포함하는 개체 또는 배열과 함께 중첩될 수 있다.
JSON은 웹 서버와 클라이언트 간의 데이터 교환에 널리 사용되며 단순성과 사용 편의성으로 인해 XML의 인기 있는 대안이 되었다.
대부분의 프로그래밍 언어와 웹 프레임워크에서 지원하므로 다재다능하고 널리 사용되는 데이터 형식입니다.

- 장점

1. 사람이 쉽게 읽고 쓸 수 있어 데이터 교환에 널리 사용됨
2. 경량으로 네트워크를 통한 데이터 전송 속도 향상
3. 대부분의 프로그래밍 언어 및 웹 프레임워크에서 광범위하게 지원되므로 기존 애플리케이션에 쉽게 통합할 수 있다.
4. 구문 분석 및 생성이 용이하여 유연하고 다양한 데이터 형식 만들기
5. 중첩된 데이터 구조를 지원하여 복잡한 데이터 표현 가능
6. 잘 정의되고 표준화되어 서로 다른 시스템 간의 호환성 보장

- 단점

1. JSON은 문자열, 숫자, 부울, 객체 및 배열과 같은 몇 가지 기본 데이터 유형만 지원하므로 데이터 유형에 대한 제한된 지원
2. 바이너리 데이터를 지원하지 않으므로 바이너리 형식으로 더 효율적으로 전송할 수 있는 데이터의 페이로드 크기가 커질 수 있다.
3. 스키마 적용이 없으므로 유효하지 않은 데이터를 더 쉽게 전송하고 처리할 수 있다.
4. 주석이 지원되지 않아 JSON 데이터를 문서화하고 주석을 추가하기가 더 어려워질 수 있다.
5. 복잡한 중첩 데이터 구조의 경우 JSON 데이터가 상당히 커져 잠재적인 성능 문제가 발생할 수 있다.

요약하면 JSON은 대부분의 프로그래밍 언어와 웹 프레임워크에서 널리 지원되는 가볍고 다양한 데이터 형식입니다.
단순성과 사용 용이성으로 인해 데이터 교환에 널리 사용되지만 데이터 유형에 대한 지원이 제한되고 스키마 적용이 없는 것과 같은 몇 가지 제한 사항이 있다.
전반적으로 JSON은 많은 유형의 애플리케이션에 적합한 신뢰할 수 있고 잘 확립된 데이터 형식입니다.

## DSL(Domain-Specific Language)

DSL(Domain-Specific Language)은 특정 도메인 또는 문제 공간을 위해 설계된 프로그래밍 언어다.
유연하고 광범위한 사용 사례에 적용할 수 있도록 설계된 범용 프로그래밍 언어와 달리 DSL은 특정 도메인에 맞게 조정되며 특정 작업에 최적화되는 경우가 많다.

DSL을 사용하면 개발자가 보다 자연스럽고 간결한 방식으로 솔루션을 표현할 수 있으므로 생산성을 높이고 오류를 줄일 수 있다.

DSL(도메인 특정 언어)에는 몇 가지 장점과 단점이 있다.

- 장점

1. 생산성 향상: DSL은 특정 도메인 내에서 사용하도록 설계되었으므로 개발자가 보다 자연스럽고 간결한 방식으로 솔루션을 표현할 수 있다. 이는 생산성 향상과 개발 시간 단축으로 이어질 수 있다.
2. 더 나은 표현력: DSL은 도메인별 용어와 구문을 사용하므로 개발자가 복잡한 모델이나 시스템을 더 쉽게 표현할 수 있다. 이것은 더 정확하고 이해하기 쉬운 코드로 이어질 수 있다.
3. 오류 감소: DSL은 도메인별 규칙과 제약을 적용하도록 설계되었기 때문에 오류와 버그의 가능성을 줄일 수 있다. 이는 보다 안정적이고 강력한 소프트웨어로 이어질 수 있다.
4. 손쉬운 유지 관리: DSL은 도메인 특정 문제를 명확하고 간결하게 표현하므로 시간이 지남에 따라 소프트웨어를 더 쉽게 유지 관리할 수 있다.
5. 협업 증가: DSL은 공통 언어를 제공하고 문제에 대한 이해를 제공하므로 개발자와 도메인 전문가 간의 협업을 증가시키는 데 도움이 될 수 있다.

- 단점

1. 제한된 적용 가능성: DSL은 특정 도메인용으로 설계되었으므로 다른 문제 영역이나 도메인에는 적용되지 않을 수 있다.
2. 높은 개발 비용: DSL 개발은 도메인과 사용자의 특정 요구 사항에 대한 깊은 이해가 필요하기 때문에 어렵고 시간이 많이 소요될 수 있다.
3. 제한된 사용자 기반: DSL은 특정 도메인에만 적용할 수 있으므로 제한된 사용자 기반을 가질 수 있다. 이로 인해 DSL에 대한 전문 지식을 갖춘 개발자를 찾기가 더 어려워질 수 있다.
4. 가파른 학습 곡선: DSL은 특히 해당 언어에서 사용되는 도메인별 개념과 용어에 익숙하지 않은 신규 사용자에게 가파른 학습 곡선을 가질 수 있다.
5. 제한된 툴링: DSL은 범용 프로그래밍 언어만큼 널리 사용되지 않기 때문에 툴링 및 지원이 제한될 수 있다.

요약하면 도메인 특정 언어에는 생산성 향상, 표현력 향상, 오류 감소, 유지 관리 용이성, 협업 증가 등 몇 가지 장점이 있다.
그러나 제한된 적용 가능성, 높은 개발 비용, 제한된 사용자 기반, 가파른 학습 곡선 및 제한된 도구 등 몇 가지 단점도 있다.
DSL 사용 여부를 결정할 때 프로젝트의 특정 요구 사항과 개발 팀의 전문성을 고려하는 것이 중요하다.

- 도메인 특정 언어의 몇 가지 예

1. SQL(Structured Query Language): SQL은 관계형 데이터베이스를 쿼리하고 관리하는 데 사용되는 DSL이다. 데이터베이스 작업에 최적화된 자체 구문 및 문법이 있다.
2. HTML(Hypertext Markup Language): HTML은 웹 페이지를 만드는 데 사용되는 DSL이다. 여기에는 웹 페이지를 구성하는 방법을 정의하는 특정 구문과 규칙 집합이 있다.
3. 정규식(Regular Expressions): 정규식은 패턴 일치 및 텍스트 검색에 사용되는 DSL이다. 패턴을 표현하고 일치시킬 수 있는 방법을 정의하는 특정 구문과 규칙 집합이 있다.
4. YAML(Yet Another Markup Language): YAML은 데이터 직렬화 및 구성에 사용되는 DSL이다. 여기에는 데이터를 사람이 읽을 수 있는 형식으로 표현하는 방법을 정의하는 특정 구문 및 규칙 집합이 있다.
5. R(프로그래밍 언어): R은 통계 계산 및 데이터 분석을 위해 특별히 설계된 프로그래밍 언어이다. 자체 구문과 데이터 작업에 최적화된 함수 집합이 있다.

이러한 각 언어는 특정 도메인 내에서 사용하도록 설계되었으며 자체 구문, 문법 및 규칙이 있다.
DSL을 사용하여 개발자는 도메인 내에서 솔루션을 보다 쉽게 ​​표현하고 보다 정확하고 안정적이며 유지 관리 가능한 소프트웨어를 만들 수 있다.

## 선언형 프로그래밍

선언적 프로그래밍은 프로그램이 어떻게 해야 하는지가 아니라 무엇을 해야 하는지에 초점을 맞추는 프로그래밍 패러다임이다.
프로그래머는 원하는 결과를 지정하고 컴퓨터는 이를 달성하는 최선의 방법을 결정한다. 선언적 프로그래밍은 종종 SQL 또는 HTML과 같은 고급 프로그래밍 언어와 연결된다.

- 장점

1. 코드는 구현보다는 결과에 초점을 맞추기 때문에 읽고 이해하기 쉽다.
2. 더 모듈화되고 재사용 가능한 코드로 이어져 유지 관리가 더 쉬울 수 있다.
3. 여러 프로세서 또는 시스템에서 병렬화 및 배포에 더 적합하다.
4. 높은 수준의 추상화로 인해 오류 및 버그 가능성 감소된다.

- 단점

1. 컴퓨터가 결과를 달성하기 위한 최선의 방법을 결정해야 하므로 속도 및 메모리 사용 측면에서 효율성이 떨어질 수 있다.
2. 일부 프로그래머가 이해하기 어려울 수 있는 더 높은 수준의 추상화가 필요하다.
3. 프로그램 흐름 및 상태에 대한 제한된 제어로 인해 디버깅이 더 어려워질 수 있다.

## 명령형 프로그래밍

명령형 프로그래밍은 특정 결과를 달성하는 방법에 초점을 맞춘 프로그래밍 패러다임이다.
즉, 프로그래머는 컴퓨터에 단계별 지침을 지정하여 수행할 작업과 수행 방법을 정확하게 알려준다.
명령형 프로그래밍은 종종 프로그래머에게 컴퓨터 하드웨어에 대한 높은 수준의 제어를 제공하는 Assembly 또는 C와 같은 저수준 프로그래밍 언어와 관련된다.

- 장점

1. 프로그램 흐름 및 상태에 대한 완전한 제어 제공된다.
2. 프로그래머가 하드웨어를 직접 제어하므로 속도와 메모리 사용 측면에서 더 효율적일 수 있다.
3. 프로세스의 각 단계를 지정하므로 프로그램 작동 방식에 대한 명확한 이해를 제공한다.

- 단점

1. 코드는 특히 더 큰 프로그램의 경우 더 복잡하고 읽고 유지하기 어려울 수 있다.
2. 코드 중복 및 덜 모듈화된 코드로 이어질 수 있다
3. 여러 프로세서 또는 시스템에 병렬화하거나 분산하기 어려움있다.
4. 명시적인 특성으로 인해 오류 및 버그가 발생하기 쉽다.

## SRP(단일 책임 원칙)

SRP(Single Responsibility Principle)는 클래스 또는 모듈이 단 하나의 책임만 가져야 하며 따라서 변경해야 하는 이유는 단 하나여야 한다는 소프트웨어 설계 원칙이다.
즉, 클래스나 모듈은 한 가지 일을 잘 수행해야 합니다.

SRP는 개발자가 모듈식, 유지 관리 및 확장 가능한 소프트웨어를 만드는 데 도움이 되도록 개발된 개체 지향 설계의 SOLID 원칙의 일부이다.

SRP를 준수함으로써 개발자는 단일 작업에 초점을 맞춘 클래스와 모듈을 생성할 수 있으므로 이해, 테스트 및 유지 관리가 더 쉬워진다.
클래스나 모듈에 하나의 책임만 있는 경우 변경해야 할 사항은 코드의 해당 영역으로 제한되므로 버그가 발생할 가능성이 줄어들고 향후 변경이 더 쉬워진다.

예를 들어 사용자 입력의 유효성 검사와 이메일 전송을 모두 담당하는 클래스를 생각해 보자.
이메일 전송 방식이 변경되면 잠재적으로 유효성 검사 논리에 영향을 미칠 수 있으며 그 반대의 경우도 마찬가지이다.
이러한 책임을 두 개의 개별 클래스로 분리하면 코드의 한 영역을 변경해도 다른 영역에 영향을 주지 않으므로 코드가 모듈화되고 유지 관리가 쉬워진다.

요약하면 단일 책임 원칙은 모듈화되고 유지 관리 가능하며 확장 가능한 코드를 촉진하는 소프트웨어 설계의 중요한 원칙이다.
단일 책임에 집중함으로써 클래스와 모듈을 더 쉽게 이해, 테스트 및 유지 관리할 수 있으므로 버그가 발생할 가능성이 줄어들고 향후 변경이 더 쉬워진다.

## Atomic Design

Atomic Design은 체계적이고 모듈화된 방식으로 사용자 인터페이스를 설계하고 구축하기 위한 방법론이다.
이 접근 방식은 Brad Frost가 개발했으며 사용자 인터페이스를 결합하여 더 복잡한 디자인을 생성할 수 있는 더 작고 재사용 가능한 구성 요소로 나눌 수 있다는 아이디어를 기반으로 한다.

"원자(atomic)"라는 용어는 화학에서 유래했으며 모든 것이 물질의 가장 작은 단위인 원자로 구성되어 있다는 생각을 나타낸다.
같은 방식으로 사용자 인터페이스는 "원자(atoms)"라고 하는 가장 작은 요소로 나눌 수 있다. 아톰의 예로는 buttons, form fields 및 icons가 있다.

그런 다음 이러한 원자를 결합하여 여러 원자로 구성된 보다 복잡한 구성 요소인 "분자(molecules)"를 만들 수 있다.
예를 들어 search form은 text input 원자와 search button 원자로 구성될 수 있다.

그런 다음 분자를 결합하여 원자와 분자를 모두 포함하는 훨씬 더 복잡한 구성 요소인 "유기체(organisms)"를 만들 수 있다.
예를 들어 헤더는 logo 분자, navigation 분자 및 search form 분자로 구성될 수 있다.

마지막으로 유기체를 결합하여 여러 유기체를 포함하는 전체 페이지 레이아웃인 "템플릿(templates)"을 만들 수 있다.
그런 다음 템플릿을 사용하여 사용자가 상호 작용하는 최종 출력인 "페이지"를 만듭니다.

Atomic Design 방법론을 사용하면 디자이너와 개발자가 유연하게 결합하여 새로운 디자인을 만들 수 있는 재사용 가능한 구성 요소 라이브러리를 만들 수 있다는 이점이 있다.
이를 통해 대규모 디자인 시스템에서 일관성을 쉽게 유지하고 코드의 중복 및 반복을 줄일 수 있다.

전반적으로 Atomic Design은 시간이 지남에 따라 쉽게 유지 관리하고 확장할 수 있는 확장 가능한 모듈식 사용자 인터페이스를 만드는 데 유용한 방법론이다.

## React component 와 props

React에서 컴포넌트는 애플리케이션 UI의 빌딩 블록이다.
구성 요소(Components)는 본질적으로 자체 기능(JavaScript 로직), 스타일 및 마크업을 캡슐화하는 재사용 가능한 코드 조각이다.

구성 요소(Components)는 기능(Functional) 구성 요소와 클래스(Class) 구성 요소의 두 가지 유형으로 나눌 수 있다.
기능적 구성 요소는 더 단순하며 상태 비저장 또는 프레젠테이션 구성 요소를 만드는 데 사용된다.
반면에 클래스 구성 요소는 사용자 상호 작용을 처리하고 자체 상태를 유지할 수 있는 상태 저장 구성 요소를 만드는 데 사용된다.

요즘은 기본적으로 함수 컴포넌트로 작성을 하고 이전에 클래스 컴포넌트에서 가지고 있던 상호작용을 처리하는 부분들이 hooks를 통해 함수형 컴포넌트에서 작성 할 수 있다.

React에서 구성 요소는 "props" 형식으로 부모 구성 요소로부터 데이터를 받을 수도 있다.
props는 속성(properties)의 약자이며 단방향 흐름에서 구성 요소 간에 데이터를 전달하는 방법이다.
props는 React에서 데이터 전달, 이벤트 핸들러 설정 또는 하위 구성 요소의 동작 구성과 같은 다양한 목적으로 사용될 수 있다.
이들은 React에서 모듈식 및 재사용 가능한 구성 요소를 구축하는 데 필수적인 부분이다.

props는 자식 구성 요소 내에서 읽기 전용으로 간주되어야 한다는 점에 유의하는 것이 중요하다. 자식 구성 요소 내에서 직접 수정하면 안 된다.