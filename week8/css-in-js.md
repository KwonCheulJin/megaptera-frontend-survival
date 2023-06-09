# 3.CSS in JS

## CSS in JS 란

CSS in JS는 기존 CSS 파일을 사용하는 대신 자바스크립트 파일 내에서 자바스크립트 구문을 사용하여 CSS 스타일을 작성하는 방식을 말한다.
개발자가 작업 중인 컴포넌트나 모듈 내에 CSS 스타일을 캡슐화할 수 있어 모듈성과 편의성을 높일 수 있는 접근 방식이다.

1. CSS와 자바스크립트의 통합(Integration of CSS and JavaScript): CSS in JS를 사용하면 일반적으로 관련 컴포넌트 로직이 있는 동일한 파일 또는 모듈 내에서 CSS 스타일이 자바스크립트 코드에 직접 작성된다. 이러한 통합을 통해 별도의 CSS 파일이 필요하지 않으며 보다 일관된 개발 환경을 제공한다.

2. 동적 스타일링(Dynamic Styling): CSS in JS는 자바스크립트 변수, 조건, 함수를 CSS 스타일 내에서 사용할 수 있도록 허용하여 동적 스타일링을 가능하게 한다.
이러한 유연성 덕분에 사용자 상호 작용, 컴포넌트 상태 또는 기타 요인에 따라 변경될 수 있는 스타일을 만들 수 있다. 또한 다양한 화면 크기와 환경에 맞게 조정되는 반응형 디자인을 쉽게 만들 수 있다.

3. 범위 지정 스타일(Scoped Styles): CSS in JS는 일반적으로 스타일이 정의된 컴포넌트 또는 모듈 내에서 스타일을 캡슐화하는 메커니즘을 제공한다.
즉, 한 컴포넌트에 정의된 스타일이 다른 컴포넌트의 스타일에 영향을 미치지 않으므로 명명 충돌과 스타일 유출의 가능성이 줄어듭니다.

4. 모듈성 및 재사용성(Modularity and Reusability): CSS in JS는 컴포넌트가 스타일을 포함할 수 있도록 허용하여 모듈성과 재사용성을 촉진한다. 따라서 컴포넌트 로직과 함께 스타일을 더 쉽게 관리하고 유지 관리할 수 있어 사용하지 않거나 충돌하는 스타일이 발생할 가능성이 줄어듭니다. 또한 애플리케이션의 여러 부분에서 컴포넌트와 관련 스타일을 쉽게 재사용할 수 있다.

5. 성능 최적화(Performance Optimization): JS 도구의 CSS는 빌드 프로세스 중에 최적화를 수행하여 불필요한 스타일을 제거하고 생성된 CSS의 전체 크기를 줄이는 경우가 많다. 이렇게 하면 브라우저에서 로드하고 구문 분석해야 하는 CSS의 양을 줄여 애플리케이션의 성능을 개선하는 데 도움이 된다.

6. 툴링 및 라이브러리(Tooling and Libraries): JS 라이브러리 및 프레임워크에는 각각 고유한 구문과 기능을 갖춘 다양한 CSS가 등장했다. 인기 있는 옵션으로는 스타일 컴포넌트, 이모션, CSS 모듈 등이 있다. 이러한 도구는 다양한 자바스크립트 프레임워크 및 라이브러리에 CSS in JS를 쉽게 통합할 수 있는 API 및 유틸리티를 제공한다.

7. CSS 기능 및 호환성(CSS Features and Compatibility): JS 라이브러리의 CSS는 선택자, 의사 클래스, 애니메이션, 미디어 쿼리, 공급업체 접두사 등 대부분의 CSS 기능을 지원하기 위해 노력한다. 하지만 일부 CSS 기능은 다르게 처리되거나 추가 폴리필이 필요할 수 있으므로 다양한 브라우저와 환경에서 JS 솔루션의 CSS 호환성을 고려하는 것이 중요한다.

글로벌 스타일 오염, 특정성 충돌, 캡슐화 부족 등 기존 CSS 개발과 관련된 몇 가지 문제를 해결할 수 있다는 점 때문에 최근 몇 년 동안 CSS in JS가 인기를 얻고 있다.
그러나 JS에서 CSS를 채택할지 여부는 팀의 친숙도, 툴링 지원, 성능 고려 사항 등의 요소를 고려하여 프로젝트의 구체적인 필요와 요구 사항을 기반으로 평가해야 한다.

## CSS

CSS는 웹 개발자가 웹 페이지의 시각적 표현을 제어할 수 있는 강력한 도구이다.
다양한 스타일 옵션과 유연성, 요소의 모양을 제어할 수 있는 기능을 제공한다.
웹 개발자는 구조와 콘텐츠(HTML)를 프레젠테이션(CSS)에서 분리하여 시각적으로 매력적이고 체계적으로 구성된 웹사이트를 만들 수 있다.

### 선택자

선택자는 특정 HTML 요소 또는 요소 그룹에 스타일을 적용하고 타겟팅할 수 있는 CSS의 기본 개념이다.
선택자는 웹 페이지에서 어떤 요소가 관련 CSS 규칙의 영향을 받을지 결정한다. CSS는 요소의 유형, 속성, 클래스 이름, ID 등을 기준으로 요소를 일치시키는 다양한 선택자를 제공한다.

1. 태그 선택자(Tag Selectors): `div`, `p` 또는 `h1`과 같은 HTML 태그 이름을 기준으로 요소를 선택한다.

2. 클래스 선택자(Class Selectors): `.my-class`와 같이 클래스 이름 뒤에 점(.)을 사용하여 할당된 클래스 이름을 기준으로 요소를 선택한다.

3. ID 선택자(ID Selectors): 해시(#) 뒤에 ID 이름(예: `#my-id`)을 사용하여 페이지에서 ID로 고유한 요소를 선택한다.

4. 속성 선택자(Attribute Selectors): 유형이 "텍스트"인 모든 입력 요소를 선택하려면 `[type="text"]`와 같이 속성을 기준으로 요소를 선택한다.

5. 의사 클래스(Pseudo-Classes): `:hover`, `:active` 또는 `:nth-child()`와 같이 문서 내 상태 또는 위치에 따라 요소를 선택한다.

6. 결합기(Combinators): 여러 선택자를 결합하여 특정 요소를 대상으로 지정한다. 일반적인 결합기에는 하위 선택자(공백), 하위 선택자(>), 인접한 형제 선택자(+) 및 일반 형제 선택자(~)가 있다.

### 박스모델

박스 모델은 콘텐츠, 패딩, 테두리 및 여백을 고려하여 웹 페이지에서 요소가 렌더링되는 방식을 설명하는 CSS의 핵심 개념이다.
상자 모델은 각 요소를 크기와 간격에 영향을 주는 다양한 속성을 가진 직사각형 상자로 취급한다.

1. 콘텐츠(Contents): 텍스트, 이미지 또는 기타 HTML 요소와 같은 요소의 실제 콘텐츠이다.

2. 패딩(Padding): 콘텐츠와 요소 테두리 사이의 공간이다. 패딩은 패딩 상단, 패딩 하단, 패딩 오른쪽, 패딩 왼쪽 또는 패딩(padding-top, padding-bottom, padding-right, padding-left or padding)과 같은 속성을 사용하여 지정할 수 있다.

3. 테두리(Border): 요소의 패딩과 콘텐츠를 둘러싸는 선이다. 테두리는 테두리 너비, 테두리 스타일, 테두리 색상(border-width, border-style, border-color)과 같은 속성을 사용하여 스타일과 크기를 지정할 수 있다.

4. 여백(Margin): 여백: 요소의 테두리 바깥쪽 공간으로 인접한 요소 사이에 공간을 만듭니다. 여백은 여백 상단, 여백 왼쪽, 여백 오른쪽, 여백 하단 또는 여백 (margin-top, margin-bottom, margin-right, margin-left or margin)과 같은 속성을 사용하여 지정할 수 있다.

### media query

미디어 쿼리는 화면 크기, 해상도, 방향 등 사용자의 기기나 뷰포트의 특성에 따라 다양한 스타일을 적용할 수 있는 CSS 기능이다.
미디어 쿼리를 사용하면 다양한 장치와 화면 크기에 맞게 레이아웃과 스타일을 조정하여 반응형 웹 디자인을 구현할 수 있다.

1. 미디어 유형(Media Type): 미디어 쿼리는 컴퓨터 화면의 경우 화면(`screen`), 인쇄 매체의 경우 인쇄(`print`), 스크린 리더의 경우 음성(`speech`) 등 다양한 미디어 유형을 타깃팅할 수 있다.

2. 미디어 기능(Media Features): 미디어 쿼리는 너비, 높이, 방향, 종횡비, 색상 등 다양한 기능을 사용하여 타겟 디바이스의 속성을 결정할 수 있다. 예를 들어 @media(max-width: 768px)는 뷰포트 너비가 768픽셀 이하일 때 스타일을 적용한다.

3. 반응형 디자인(Responsive Design): 미디어 쿼리는 일반적으로 반응형 디자인을 만들기 위해 CSS 그리드 및 Flexbox와 함께 사용된다. 화면 크기나 기기 방향에 따라 서로 다른 스타일을 정의하면 웹 페이지의 레이아웃과 프레젠테이션이 최적의 사용자 경험을 제공하도록 조정할 수 있다.

### Flexbox

플렉스박스: 플렉시블 박스 레이아웃의 줄임말인 플렉스박스는 요소를 행이나 열로 배열할 수 있는 1차원 레이아웃 시스템이다. 공간을 분배하고, 요소를 정렬하고, 크기와 순서를 제어할 수 있는 유연하고 동적인 방법을 제공한다.
Flexbox의 주요 기능 및 개념은 다음과 같다:

1. 플렉스 컨테이너(Flex Container): 플렉스 항목을 포함하는 상위 요소이다. 컨테이너에 CSS 속성 `display: flex` 또는 `display: inline-flex`를 적용하면 플렉스 컨테이너가 된다.

2. 플렉스 항목(Flex Items): 플렉스 레이아웃의 영향을 받는 플렉스 컨테이너 내의 하위 요소이다. 플렉스 항목은 컨테이너 내의 사용 가능한 공간에 맞게 크기를 늘리거나 줄이거나 고정할 수 있다.

3. 주축 및 교차 축(Main Axis and Cross Axis): 플렉스박스는 주축과 교차 축의 두 축을 따라 작동한다. 주축은 행(왼쪽에서 오른쪽)(row (left-to-right)) 또는 열(위에서 아래로)(column (top-to-bottom)로 설정할 수 있는 플렉스 방향(flex-direction) 속성에 의해 결정된다. 십자축은 주축에 수직이다.

4. 유연성(Flexibility): 플렉스박스를 사용하면 사용 가능한 공간에 따라 플렉스 항목을 늘리거나 줄일 수 있다. 플렉스 성장(flex-grow), 플렉스 축소(flex-shrink) 및 플렉스 기준(flex-basis) 속성은 플렉스 항목의 크기를 조정하는 방법을 제어한다.

5. 정렬 및 정당화(Alignment and Justification): Flexbox는 콘텐츠 맞춤(justify-content) 및 항목 정렬(align-items과 같은 속성을 제공하여 주축 및 교차 축을 따라 플렉스 항목의 정렬 및 분포를 제어한다. 이를 통해 플렉스 컨테이너 내에서 요소를 쉽게 중앙에 배치하고 간격을 조정하고 정렬할 수 있다.

[이번에야말로 CSS Flex를 익혀보자](https://studiomeal.com/archives/197)

### Grid

일반적으로 CSS 그리드라고 알려진 CSS 그리드 레이아웃은 복잡한 그리드 기반 레이아웃을 만들 수 있는 2차원 레이아웃 시스템이다.
행, 열, 그리드 내 요소의 정렬 및 배치를 정밀하게 제어할 수 있다.

1. 그리드 컨테이너(Grid Container): 그리드 항목을 포함하는 부모 요소이다. 컨테이너에 CSS 속성 `display: grid`를 적용하면 그리드 컨테이너가 된다.

2. 그리드 항목(Grid Items): 그리드 컨테이너 내의 자식 요소이다. 그리드 항목은 선 기반 배치 또는 그리드 영역 배치를 사용하여 그리드 내에 배치된다.

3. 그리드 트랙(Grid Tracks:): 그리드를 구성하는 가로 및 세로 트랙이다. 트랙은 그리드 템플릿 열(grid-template-columns) 및 그리드 템플릿 행(grid-template-rows) 속성을 사용하여 명시적으로 정의하거나 그리드 항목을 배치하여 암시적으로 만들 수 있다.

4. 그리드 선(Grid Lines): 그리드를 행과 열로 나누는 선이다. 이 선을 참조하여 그리드 항목을 배치하고 정렬할 수 있다.

5. 그리드 영역(Grid Areas): 그리드 항목에 할당할 수 있는 그리드 내의 명명된 영역이다. 그리드-템플릿-영역(grid-template-areas) 속성을 사용하여 그리드 영역을 지정하면 그리드 내에서 그리드 항목을 쉽게 배치하고 재정렬할 수 있다.

6. 정렬 및 간격(Alignment and Spacing): CSS 그리드에는 그리드 셀 내에서 그리드 항목의 정렬 및 간격을 제어할 수 있는 justify-items, align-items, justify-content, align-content와 같은 속성이 제공된다. 이를 통해 요소의 위치 및 배열을 정밀하게 제어할 수 있다.

7. 반응형 디자인(Responsive Design): CSS 그리드를 미디어 쿼리와 결합하여 다양한 화면 크기와 방향에 맞게 조정되는 반응형 레이아웃을 만들 수 있다. 그리드 템플릿을 수정하고 항목 배치를 조정하여 사용 가능한 공간에 따라 다양한 레이아웃을 만들 수 있다.

[이번에야말로 CSS Grid를 익혀보자](https://studiomeal.com/archives/533)
