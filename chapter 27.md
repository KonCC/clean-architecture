27장 '크고 작은 모든' 서비스들
서비스 지향 아키텍쳐와 마이크로서비스 아키텍쳐가 최근 큰 인기를 끄는 이유

서비스를 사용하면 상호결합이 철저하게 분리되어 있고, 개발과 배포 독립성을 지원하는 것처럼 보인다.
하지만 일부만 맞는 말이다.

서비스 아키텍쳐?
프로세스나 플랫폼 경계를 가로지르는 함수 호출에 지나지 않는 '서비스' 라는 것은 아키텍처 관점에서

아키텍쳐적으로 중요한 서비스도 있지만, 중요하지 않은 서비스도 존재한다.

이 중 전자를 살펴보자.

서비스의 이점?
최근 인기를 끄는 서비스 아키텍쳐에 대해 이의를 제기해보자.

결합 분리의 오류
시스템을 서비스로부터 분리함으로서 얻는 이점? -> 서비스 사이의 결합이 확실히 분리된다.

하지만 개별 변수 수준에서는 결합이 분리되어도, 프로세서 내의 또는 네트워크 상의 공유 데이터에 의해

더욱 강력하게 결합되어 버린다.

개발 및 배포 독립성의 오류
데브옵스 관점에서 전담틱이 각 서비스를 작성하고 유지보수하며 운영하는 책임을 질 수 있다.

그러나 대규모 엔터프라이즈 시스템은 서비스 기반 시스템 외에도, 모노리틱, 컴포넌트 기반 시스템으로도

구축 가능하다. 즉, 서비스가 유일한 선택지가 아니다.

그리고 서비스라고 해서 항상 독립적으로 개발, 배포, 운영할 수 있는 것 또한 아니다.

야옹이 문제

서비스가 모두 결합되어있어 위에서 묘사된 것과 같은 종류의 기능적 분해는 새로운 기능이 기능적 행위를 횡단하는 상황에 매우 취약하다.

➡️서비스 지향이든 아니든, 모든 소프트웨어 시스템이 직면하게 될 횡단 관심사가 지닌 문제.

객체가 구출하다

하지만 컴포넌트 기반 아키텍쳐에서 SOLID 설계 원칙대로 설계했다면, 위와 같이

배차에 특화된 로직은 Rides 컴포넌트로 추출되고, 야옹이 신규 기능은 Kittens 컴포넌트에 들어간다.

두 신규 컴포넌트는 의존성 규칙을 준수하고, 다른 컴포넌트들은 변경이 필요하지 않아서,

야옹이 기능은 결합이 분리되며 독립적으로 개발 배포가 가능하다.

컴포넌트 기반 서비스
서비스또한 SOLID 원칙대로 설계할 수 있고, 컴포넌트 구조를 갖출 수 있어 기존 컴포넌트를 변경하지 않고도

새로운 컴포넌트를 추가할 수 있다.

각 서비스의 내부가 자신만의 컴포넌트 설계로 되어 있어 파생 클래스를 만드는 방식으로 신규 기능 추가 가능하다.

횡단 관심사
아키텍쳐 경계는 서비스 사이에 있지 않고, 서비스를 컴포넌트 단위로 분할한다.

아키텍처경계는 서비스 사이에 존재하지 않으며, 아키텍처 경계를 정의하는것은 서비스 내에 위치한 컴포넌트이다.

결론
서비스는 아키텍처적으로 그리 중요한 요소는 아니다.