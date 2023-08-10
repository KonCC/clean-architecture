# 6장

우리가 함수형 언어를 쓰지 않는다면 , race condition , deadlock , concurrenct update에서 자유롭지 못하다.

## 가변성의 분리

아키텍쳐를 설계할 때, 가변 컴포넌트와 불변 컴포넌트를 분리하는 방식으로 동시성 문제를 해결 가능하다.

[##_Image|kage@deTwP3/btsqJryVbKi/p4LZCLbtLSKOy4tMkXG5vk/img.png|CDM|1.3|{"originWidth":696,"originHeight":342,"style":"alignCenter"}_##]

상태 변경은 컴포넌트를 갖가지 동시성 문제에 노출하는 꼴이므로, 흔히 **트랜잭션 메모리** transactional memory 와 같은 실천법을 사용하여 동시 업데이트와 경합 조건 문제로부터 가변 변수를 보호한다.

트랜젝션 메모리란 ,, ACID를 준수하는 메모리

가능한 한 많은 처리를 불변 컴포넌트로 옮기는 것이 현명한 아키텍트이다.

## 이벤트 소싱

상태가 아닌 트랜잭션을 저장하는 전략 .

무한한 저장공간과 처리 능력이 필요해 힘들어 보이지만,현대의 소스 코드 버전 관리 시스템등은 이미 사용하는 중인 전략

[##_Image|kage@Uw9wZ/btsqM8YWp1b/dIeukqoJn15yAXkSDANv6K/img.png|CDM|1.3|{"originWidth":1064,"originHeight":554,"style":"alignCenter"}_##]

## 결론

- 구조적 프로그래밍은 제어흐름의 직접적인 전환에 부과되는 규율이다.
- 객체 지향 프로그래밍은 제어흐름의 간접적인 전환에 부과되는 규율이다.
- 함수형 프로그래밍은 변수 할당에 부과되는 규율이다.
