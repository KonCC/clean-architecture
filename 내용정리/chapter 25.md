## 25장 계층과 경계

시스템은 세가지 컴포넌트 (UI,업무 규칙, 데이터베이스)로 구성되어있다고 생각할 수 있지만,

실제로는 훨씬 많다.

### 움퍼스 사냥 게임

 게임 규칙은 게임의 상태를 영속성을 가지는 특정한 데이터 구조로 저장한다.

![image](https://github.com/KonCC/clean-architecture/assets/102205852/647246f5-163f-4f36-ba4b-ca7075f04f31)


UI 컴포넌트가 어떤 언어를 사용해도 게임 규칙을 재사용 가능.

![image](https://github.com/KonCC/clean-architecture/assets/102205852/e39a00c5-2123-47a6-862d-51fd77f9cad4)

데이터 저장소 또한, 고수준인 게임 규칙을 의존하는 형태이다.

### 클린 아키텍처?

잠재된 아키텍쳐 경계를 존재할 수 있다. 이를 그림으로 나타내면 다음과 같다.

![image](https://github.com/KonCC/clean-architecture/assets/102205852/88d2ea87-8d1e-4b61-bf9f-4121af20eeec)


점선으로 된 테두리 : API를 정의하는 추상 컴포넌트

해당 API는 위나 아래의 컴포넌트가 대신 구현한다.

그리고 api는 구현하는 쪾이 아닌, 사용하는 쪽에 정의되고 소속된다. 

EX) Game Rules 내부 코드에서 사용하나 Language 내부 코드에서 구현하는 다형적 Boundary interface가 존재한다.

이 모든 경우에 해당 Boundary 인터페이스가 정의하는 API는

의존성 흐름의 상위에 위치한 컴포넌트에 속함.

![image](https://github.com/KonCC/clean-architecture/assets/102205852/17c212d3-75fb-486e-9bb6-130f8ebac6ae)


순전히 API 컴포넌트에만 집중하여 다이어그램을 단순화하면 다음과 같다.

GameRules가 최상위 수준 정책의 컴포넌트이므로 가장 위쪽에 위치하고 화살표가 위로 맞춰져있다.

### 흐름 횡단하기

![image](https://github.com/KonCC/clean-architecture/assets/102205852/b796cb9c-9b57-4d2b-8712-f33d803bcf0a)


하지만 항상 흐름이 두 가지인것은 아니다. 예를들어 해당 게임이 온라인 게임이 된다면,

다음과 같이 네트워크 컴포넌트 또한 추가된다.

### 흐름 분리하기

![image](https://github.com/KonCC/clean-architecture/assets/102205852/323d4044-92ae-4b17-9c6e-189f6a7e4384)


게임 규칙중 일부인 지도 관련 메커니즘을 처리하는 MoveManagement를 추가한 경우

지도규칙에 의해 플레이어의 지도 관련 사건을 처리함.

사건이 발생하면 MoveManagement은 이를 판단한 후 고수준인 PlayerManagement 정책에게 알려 플레이어의 상태를 관리하도록 한다.

이 둘을 분리하는 API가 필요할까? 아직은 알 수 없다.

![image](https://github.com/KonCC/clean-architecture/assets/102205852/2a2e6c46-d828-498b-bf5e-717d2ab8ed2d)


마이크로서비스 API추가.

대규모 플레이어가 동시에 플레이하는 경우, Player Management는 접속된 모든 Move Management 컴포넌트에 API를 제공한다. 따라서 위와 같이 아키텍쳐 경계를 만들어 시나리오를 묘사할 수 있다.

### 결론

아키텍쳐 경계는 어디에나 존재할 수 있다.

그러나 추상화를 미리 진행해서도 안되고, 나중에 다시 추가해서도 안된다.

능숙한 아키텍트라면 비용을 산정하고 어디에 아키텍쳐 경계를 두어야 할지 주의를 기울여 결정해야 한다.
