# 2.TSyringe

## TSyringe

TSyringe는 인기 있는 TypeScript용 DI(의존성 주입) 컨테이너 라이브러리이다.
이를 통해 개발자는 제어 역전(IoC) 및 DI 원칙에 따라 애플리케이션 내에서 의존성을 관리하고 해결할 수 있다.
클래스 또는 서비스 인스턴스의 생성 및 검색을 처리하는 간단하고 효율적인 방법을 제공하여 모듈식 및 유지 관리 가능한 코드를 촉진한다.

TSyringe의 주요 기능 및 개념

1. 의존성 주입(Dependency Injection): TSyringe는 의존성 주입 패턴을 구현하는 데 도움이 된다. 여기서 클래스의 의존성은 클래스 자체 내에서 생성되지 않고 외부에서 제공된다. 이는 느슨한 결합, 테스트 가능성 및 모듈성을 촉진한다.
2. 컨테이너(Container): Container 클래스는 TSyringe의 핵심이다. 의존성의 Registration 및 해결을 관리하는 DI Container 역할을 한다. 클래스/인터페이스와 해당 구현 간의 매핑을 유지한다.
3. 등록(Registration): TSyringe를 사용하려면 의존성을 Container에 Registration해야 한다. Registration은 토큰(클래스 또는 인터페이스)을 구현과 연결하는 register 메서드를 사용하여 수행할 수 있다.
4. 해결(Resolution): TSyringe는 resolve 메서드를 사용하여 의존성을 해결한다. 토큰을 인수로 사용하고 해당 구현의 인스턴스를 반환한다. TSyringe는 자동으로 의존성을 재귀적으로 해결하여 필요한 모든 의존성을 주입한다.
5. 싱글톤(Singletons): TSyringe는 Singletons 인스턴스를 지원한다. registerSingleton 메소드를 사용하여 클래스의 단일 인스턴스가 생성되고 확인될 때마다 공유된다.
6. 범위 지정 인스턴스(Scoped Instances): TSyringe는 개체의 수명 주기를 제어할 수 있도록 Scoped Instances를 지원한다. 범위는 'createScope' 메서드를 사용하여 만들 수 있으며 범위 내에 Registration된 인스턴스는 해당 범위에 연결된다. 범위가 삭제되면 범위 내의 인스턴스도 삭제된다.
7. 데코레이터(Decorators): TSyringe는 의존성의 Registration 및 해결을 단순화하는 Decorators를 제공한다. @injectable Decorators는 클래스를 주입 가능한 것으로 표시하는 데 사용되는 반면 @inject Decorators는 클래스 속성 또는 생성자 매개 변수에 의존성을 주입하는 데 사용된다.
8. 커스텀 리졸버(Custom Resolvers): TSyringe는 Custom Resolvers을 구현하여 해결 과정을 맞춤화할 수 있다. 사용자 지정 해석기는 Container에 Registration할 수 있으며 특정 유형의 해석을 처리하는 데 사용할 수 있다.

TSyringe를 사용 시 이점

- 모듈화 및 유지보수성(Modularity and Maintainability): TSyringe는 의존성 관리를 용이하게 하여 모듈식 설계를 촉진한다. 전체 코드베이스에 영향을 주지 않고 구현을 교환하고 의존성을 수정하는 것이 더 쉬워진다.
- 테스트 가능성(Testability): TSyringe는 의존성을 분리하고 쉽게 모방하거나 대체할 수 있는 기능을 제공하여 코드의 테스트 가능성을 향상시킵니다. 모의 의존성이 간단해져서 더 효과적인 단위 테스트가 가능해진다.
- 코드 구성(Code Organization): TSyringe는 의존성 Registration을 명확하게 정의하고 중앙 집중화하여 코드를 구성하는 데 도움이 된다. 이렇게 하면 애플리케이션 전체에서 의존성을 쉽게 찾고 관리할 수 있다.
- 타입 안전성(Type Safety): TSyringe는 TypeScript용으로 특별히 설계되었기 때문에 유형 시스템을 활용하여 해결 프로세스 중에 유형 안전성을 제공한다. TypeScript의 유형 검사는 의존성이 올바르게 Registration되고 삽입되었는지 확인한다.

## 의존성 주입(Dependency Injection)

의존성 주입(DI)은 의존성을 사용하는 클래스에서 의존성의 생성 및 관리를 분리하여 느슨한 결합 및 모듈식 코드를 촉진하는 소프트웨어 디자인 패턴이다.
DI에서는 클래스가 의존성을 직접 생성하는 대신 일반적으로 생성자 매개 변수 또는 속성 설정자를 통해 외부에서 의존성을 제공한다.
이렇게 하면 클래스는 의존성이 생성되는 방법이나 종속 항목의 출처에 대한 세부 정보를 알 필요가 없다.

의존성 주입의 주요 목표는 응용 프로그램의 유지 관리 가능성, 테스트 가능성 및 유연성을 향상시키는 것이다.
클래스 간 결합을 줄여 코드 유지 관리를 더 쉽게 할 수 있으므로 소비하는 클래스에 영향을 주지 않고 의존성을 더 쉽게 수정하거나 교체할 수 있다.
또한 개별 구성 요소의 격리된 테스트를 위해 모의 또는 스텁 의존성을 주입하여 단위 테스트를 용이하게 한다. 또한 DI는 의존성을 통해 클래스 구성을 활성화하여 모듈성을 촉진하여 응용 프로그램을 더 쉽게 조립하고 구성할 수 있도록 한다.

의존성 주입에는 세 가지 일반적인 유형

1. 생성자 주입(Constructor Injection): Constructor를 통해 의존성이 클래스에 전달된다. 클래스는 의존성을 Constructor 매개 변수로 선언하고 의존성은 클래스가 인스턴스화될 때 제공된다. Constructor Injection은 클래스를 사용하기 전에 의존성이 충족되도록 한다.
2. Setter 주입(Setter Injection): 의존성은 setter 메서드를 통해 클래스에 설정된다. 클래스는 각 의존성에 대한 setter 메서드를 제공하며 의존성은 클래스가 인스턴스화된 후에 설정된다. Setter Injection은 클래스가 생성된 후 변경할 수 있는 선택적 또는 동적 의존성을 허용한다.
3. 메소드 주입(Method Injection): 메서드 매개변수를 통해 클래스에 의존성을 제공한다. 클래스는 특정 의존성을 필요로 하는 메서드를 정의하고 의존성은 메서드가 호출될 때 메서드 인수로 전달된다. 메서드 주입은 클래스의 나머지 부분과 비교하여 고유한 의존성이 있는 특정 메서드에 유용한다.

의존성 주입 사용 시 이점

- 느슨한 결합(Loose Coupling): DI는 구체적인 구현에 대한 직접적인 의존성을 제거하여 클래스 간의 결합을 줄인다. 이렇게 하면 소비하는 클래스에 영향을 주지 않고 의존성을 수정하거나 교체하기가 더 쉬워진다.
- 테스트 가능성(Testability): DI는 테스트 중에 모의 또는 스텁 의존성을 삽입할 수 있도록 하여 단위 테스트를 용이하게 한다. 이를 통해 보다 효과적이고 신뢰할 수 있는 테스트를 위해 구성 요소를 격리할 수 있다.
- 모듈화 및 재사용성(Modularity and Reusability): DI는 의존성을 통해 클래스 구성을 장려하여 모듈화를 촉진한다. 클래스를 쉽게 어셈블하고 다양한 의존성을 사용하여 구성할 수 있으므로 코드를 더 재사용 가능하고 유연하게 만들 수 있다.
- 구성 유연성(Configuration Flexibility): 구성을 외부화하고 의존성을 생성함으로써 DI는 유연한 구성 옵션을 허용한다. 의존성을 쉽게 구성하고 전환할 수 있으므로 애플리케이션 요구 사항에 따라 다양한 동작 또는 구성을 사용할 수 있다.
- 단일 책임 원칙(Single Responsibility Principle): DI는 의존성 생성 및 의존성 사용 문제를 분리하여 단일 책임 원칙을 준수하도록 돕다. 클래스는 핵심 책임에 초점을 맞추는 반면 의존성 생성 및 관리는 별도의 구성 요소에 위임된다.

## reflect-metadata

reflect-metadata는 런타임에 리플렉션 기능을 제공하는 TypeScript 라이브러리이다.
이를 통해 개발자는 클래스, 속성, 메서드 및 매개 변수에 메타데이터 주석을 추가하고 런타임 중에 해당 메타데이터를 검색할 수 있다.
이 라이브러리는 ECMAScript 6에 도입된 내장 JavaScript API인 Reflect API를 활용한다.

리플렉션은 프로그램이 런타임에 자체 구조와 동작을 검사, 검사 및 수정하는 기능을 말한다.
클래스, 속성, 메서드 및 함수 매개 변수와 같은 코드 요소를 동적으로 검사하고 조작할 수 있다.
개발자는 reflect-metadata를 사용하여 메타데이터에 주석을 달고 검색하여 애플리케이션의 유연성과 확장성을 향상할 수 있다.

reflect-metadata의 주요 개념 및 기능

1. 메타데이터(Metadata): 메타데이터는 코드 요소에 첨부할 수 있는 추가 정보 또는 주석이다. reflect-metadata를 사용하면 데코레이터를 사용하거나 Reflect API를 사용하여 수동으로 메타데이터를 설정하여 클래스, 속성, 메서드 및 매개 변수에 메타데이터를 추가할 수 있다.
2. 데코레이터(Decorators): 데코레이터는 해당 요소에 동작을 수정하거나 추가하기 위해 클래스, 속성, 메서드 또는 매개 변수에 첨부할 수 있는 특수 선언이다. reflect-metadata는 데코레이터와 함께 작동하여 장식된 요소와 관련된 메타데이터를 저장하고 검색한다.
3. Reflect API: reflect-metadata 라이브러리는 메타데이터에 액세스하기 위한 일련의 반사 메서드를 제공하는 Reflect API를 활용한다. 이러한 메소드에는 Reflect.defineMetadata, Reflect.hasMetadata, Reflect.getMetadata, Reflect.getOwnMetadata 등이 포함된다. 이러한 메서드를 사용하면 코드 요소와 연결된 메타데이터를 설정하고 검색할 수 있다.
4. 사용법(Usage): reflect-metadata를 사용하려면 npm 또는 yarn을 통해 라이브러리를 설치하고 TypeScript 프로젝트로 가져와야 한다. 그런 다음 데코레이터를 클래스, 속성, 메서드 또는 매개 변수에 적용하고 Reflect API를 사용하여 런타임 중에 연결된 메타데이터를 검색하거나 수정할 수 있다.

reflect-metadata 사용 시 이점

- 메타데이터 주석(Metadata Annotations): reflect-metadata를 통해 개발자는 코드 요소에 메타데이터 주석을 첨부할 수 있다. 이 메타데이터는 구성, 의존성 주입 또는 클래스 및 메서드의 런타임 분석과 같은 다양한 용도로 사용할 수 있다.
- 동적 동작(Dynamic Behavior): 애플리케이션은 리플렉션 및 메타데이터를 활용하여 코드 요소와 연결된 메타데이터를 기반으로 동적 동작을 나타낼 수 있다. 이를 통해 런타임 사용자 지정 및 확장이 가능한다.
- 프레임워크 및 라이브러리와의 통합(Integration with Frameworks and Libraries): Angular, TypeORM 또는 NestJS와 같은 많은 프레임워크 및 라이브러리는 '반사 메타데이터'를 활용하여 의존성 주입, 개체 관계형 매핑 또는 선언적 프로그래밍과 같은 고급 기능을 활성화한다. 'reflect-metadata'를 이해하고 사용하면 이러한 프레임워크 작업 능력을 향상시킬 수 있다.

## sington (싱글톤)

소프트웨어 개발에서 싱글톤 패턴은 클래스의 인스턴스화를 단일 개체로 제한하는 생성 디자인 패턴이다.
전체 응용 프로그램에서 클래스의 인스턴스가 하나만 있는지 확인하고 해당 인스턴스에 대한 글로벌 액세스 지점을 제공한다.

Singleton 패턴의 주요 특징 및 개념

1. 단일 인스턴스(Single Instance): Singleton 패턴은 주어진 시간에 클래스의 인스턴스가 하나만 생성되고 애플리케이션에 존재하도록 보장한다.
2. 글로벌 액세스(Global Access): Singleton은 인스턴스에 대한 글로벌 액세스 지점을 제공하여 다른 개체 또는 구성 요소가 쉽게 액세스하고 사용할 수 있도록 한다.
3. 비공개 생성자(Private Constructor): 외부 인스턴스화를 방지하기 위해 Singleton 클래스에는 일반적으로 비공개 생성자가 있다. 이렇게 하면 new 키워드를 사용하여 클래스를 직접 인스턴스화할 수 없다.
4. 정적 인스턴스(Static Instance): Singleton 클래스는 일반적으로 클래스의 단일 인스턴스를 보유하는 정적 멤버 변수를 포함한다. 이 멤버는 정적 메서드 또는 속성을 통해 액세스된다.
5. 초기화 지연(Lazy Initialization): Singleton 인스턴스는 종종 느리게, 즉 처음 요청될 때만 생성된다. 이 접근 방식은 실제로 필요할 때까지 인스턴스화를 연기하여 리소스 사용을 최적화한다.
6. 스레드 안전성(Thread Safety): 다중 스레드 환경에서는 스레드 안전성을 보장하기 위해 특별한 주의를 기울여야 한다. 동기화 메커니즘 또는 스레드로부터 안전한 초기화 기술을 사용하여 동시 시나리오에서도 하나의 인스턴스만 생성되도록 해야 한다.

Singleton 패턴의 이점 및 사용 사례

1. 전역 액세스(Global Access): 싱글톤 패턴은 애플리케이션 어디에서나 클래스의 단일 인스턴스에 액세스할 수 있는 편리한 방법을 제공한다. 이는 구성 관리자, 로깅 서비스 또는 데이터베이스 연결과 같은 특정 기능을 담당하는 개체가 하나만 있어야 하는 경우에 유용할 수 있다.
2. 자원 관리(Resource Management): 단일 인스턴스를 보장함으로써 Singleton 패턴은 제한적이거나 값비싼 자원을 효과적으로 관리하는 데 도움이 된다. 예를 들어 생성 비용이 많이 드는 데이터베이스 연결을 한 번 인스턴스화하여 애플리케이션 전체에서 재사용할 수 있다.
3. 일관성 및 제어(Consistency and Control): 싱글톤 패턴은 개체의 상태 및 동작에 대한 일관성과 제어를 유지하는 데 도움이 된다. 인스턴스가 하나뿐이므로 객체에 대한 변경 사항은 객체에 액세스하는 모든 구성 요소에서 즉시 볼 수 있다.
4. 의존성 주입(Dependency Injection): 의존성 주입 프레임워크에서 싱글톤을 사용하여 인스턴스를 명시적으로 전달하지 않고 여러 소비자에게 클래스의 단일 인스턴스를 제공할 수 있다.

Singleton 패턴의 잠재적인 단점과 주의 사항

1. 글로벌 상태(Global State): 싱글톤을 사용하면 글로벌 상태가 도입되어 코드를 테스트, 이해 및 유지 관리하기가 더 어려워질 수 있다. 긴밀한 결합으로 이어지고 애플리케이션의 확장성과 모듈성을 방해할 수 있다.
2. 오용 가능성(Potential Misuse): 싱글톤 사용은 오용 및 남용될 수 있으므로 신중하게 고려해야 한다. 클래스에 실제로 단일 인스턴스가 필요한지 여부와 의존성 주입 또는 팩토리와 같은 대체 패턴이 더 적합한지 여부를 평가하는 것이 중요한다.
3. 테스트 과제(Testing Challenges): 싱글톤 인스턴스는 대체하거나 모의하기 어려울 수 있는 의존성을 도입하므로 단위 테스트를 더욱 어렵게 만들 수 있다. Singleton 의존성 주변에서 테스트 가능한 코드를 설계하려면 주의를 기울여야 한다.
4. 동시성 고려 사항(Concurrency Considerations): 다중 스레드 환경에서 Singleton 인스턴스는 동시 액세스를 적절하게 처리하도록 설계되어야 한다. 경쟁 조건을 피하고 스레드 안전을 보장하려면 동기화 메커니즘 또는 지연 초기화 기술을 사용해야 한다.
