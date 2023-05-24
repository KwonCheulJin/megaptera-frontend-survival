# 1.Routing

## HTML DOM API

### Location

'window' 객체의 'location' 속성은 웹 개발에서 URL을 편리하게 작업할 수 있는 방법을 제공한다.
개발자는 해당 속성에 액세스하여 현재 URL에 대한 정보를 검색하거나, URL의 일부를 수정하거나, 새 URL로 이동할 수 있으므로 웹 애플리케이션에서 동적이고 인터랙티브한 동작을 구현할 수 있다.

1. `location.href`: 이 속성은 현재 웹 페이지의 전체 URL을 나타낸다. 읽기와 수정이 모두 가능하다.
2. `location.protocol`: 이 속성은 URL의 프로토콜 부분(예: "http:" 또는 "https:")을 반환한다. 현재 페이지의 프로토콜을 확인하거나 수정할 때 유용한다.

3. `location.host` 및 `location.hostname`: 이 속성은 URL의 도메인 또는 호스트 이름을 반환한다. 예를 들어 "example.com"은 URL "<https://example.com"의> 호스트 이름이다. `location.host` 속성에는 지정된 경우 포트 번호도 포함된다.

4. `location.pathname`: 이 속성은 URL의 경로와 파일 이름을 반환한다. 예를 들어 URL "<https://example.com/path/file.html"에서> "location.pathname"은 "/path/file.html"이 된다.

5. `location.search`: 이 속성은 물음표("?") 및 모든 매개변수를 포함하여 URL의 쿼리 문자열 부분을 반환한다. 예를 들어 "<https://example.com/search?q=apple>" URL에서 "location.search"는 "?q=apple"이 된다.

6. `location.hash`: 이 속성은 조각 식별자 또는 해시 기호("#") 뒤에 오는 URL의 일부를 반환한다. 특정 섹션으로 이동하기 위한 페이지 내 앵커 링크에 자주 사용된다.

### pathname

URL 컨텍스트에서 `pathname`은 웹 서버에 있는 리소스의 경로와 파일 이름을 나타내는 URL 부분을 나타낸다. 서버의 파일 시스템 내에서 리소스의 계층 구조 및 위치에 대한 정보를 제공한다.

`pathname`은 특히 `window.location` 개체 내에서 HTML DOM API에 있는 "location" 개체의 속성이다. window.location.pathname과 같은 `pathname` 속성을 사용하여 액세스할 수 있다.

`pathname` 핵심 사항

1. 구조 및 형식(Structure and Format): `pathname`은 슬래시("/")로 시작하는 문자열이며 웹 서버의 파일 또는 디렉토리에 대한 경로를 나타낸다. 슬래시("/")로 구분된 여러 수준의 디렉토리가 포함될 수 있다. 예를 들어 URL "<https://example.com/path/file.html"에서> `pathname`은 "/path/file.html"이다.

2. 파일 이름 및 확장자(File Names and Extensions): URL이 특정 파일을 나타내는 경우 `pathname`에는 일반적으로 파일 이름과 해당 확장자가 포함된다. 위의 예에서 "file.html"은 확장자가 ".html"인 파일 이름이다.

3. 디렉토리 구조(Directory Structure): URL이 디렉토리 또는 중첩된 디렉토리 구조를 나타내는 경우 `pathname`에는 경로의 디렉토리 이름이 포함된다. 예를 들어 URL "<https://example.com/path/subdirectory/file.html"에서> `pathname`은 "/path/subdirectory/file.html"이며 리소스가 다음 위치에 있음을 나타낸다. ("path" 디렉토리 내에 있는 "subdirectory" 디렉토리)

4. 후행 슬래시(Trailing Slash): 어떤 경우에는 `pathname`이 후행 슬래시("/")로 끝나서 URL이 특정 파일이 아닌 디렉토리를 나타냄을 나타낼 수 있다. 예를 들어, "<https://example.com/directory/"는> "directory" 디렉터리를 나타내는 것을 나타내기 위해 `pathname`에 후행 슬래시가 있다.

5. 쿼리 매개변수 및 해시(Query Parameters and Hash): `pathname`에는 쿼리 매개변수(물음표 "?" 뒤 부분) 또는 해시 조각(해시 기호 "#" 뒤 부분)이 포함되지 않다. `pathname`은 특히 리소스의 경로와 파일 이름을 나타내며 쿼리 매개 변수와 해시는 URL의 별도 구성 요소이다.
