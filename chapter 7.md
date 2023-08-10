# 7장~ 11장을 들어가며

## SOLID 원칙의 목적

- 변경에 유연하다.
- 이해하기 쉽다.
- 많은 소프트웨어 시스템에 사용될 수 있는 컴포넌트의 기반이 된다.

# 7장

## SRP : 단일 책임 원칙

모듈이 아닌 함수가 , 반드시 단 하나의 일만 해야 한다는 원칙으로 오해할 수 있지만,

진정한 SRP는 하나의 모듈은 오직 하나의 액터에 대해서만 책임져야 한다는 것.

여기서 모듈은 단순히 소스 파일로 볼 수 있다.

## 징후 1: 우발적 중복

[##_Image|kage@GUKz0/btsqRf4eD1L/d8unaOYY2FquBK2bQgcrx0/img.png|CDM|1.3|{"originWidth":690,"originHeight":343,"style":"alignCenter"}_##]

위 Employee 클래스는 SRP를 위반하는데, 이들 세 가지 메서드가 서로 매우 다른 세 명의 액터를 책임지기 때문이다.

- calculatePay(): 회계팀에서 기능을 정의하며, CFO 보고를 위해 사용한다.
- reportHours(): 인사팀에서 기능을 정의하며, COO 보고를 위해 사용한다.
- save(): 데이터베이스 관리자 DBA 가 기능을 저의하고, CTO 보고를 위해 사용한다.

예를 들어 calculatePay() 메서드와 reportHours() 메서드가 초과 근무를 제외한 업무 시간을 계산하는 알고리즘을 공유한다고 해보자.

그리고 개발자는 코드 중복을 피하기 위해 이 알고리즘을 regularHours()라는 메서드에 넣었다고 해보자.

[##_Image|kage@csKloI/btsqPZm7VNQ/1iDyPy4HFccwoSndw0Ph1k/img.png|CDM|1.3|{"originWidth":693,"originHeight":298,"style":"alignCenter"}_##]

이제 CFO 팀에서 초과 근무를 제외한 업무 시간을 계산하는 방식을 약간 수정하기로 결정했다고 하자. 반면 인사를 담당하는 COO 팀에서는 초과 근무를 제외한 업무 시간을 CFO 팀과는 다른 목적으로 사용하기 때문에 이 같은 변경을 원하지 않는다고 해보자.

이때, CFO 팀에서는 COO 팀또한 regularHours를 사용한다는 사실을 몰랐고, 수정하게 된다.

그리고 COO 팀은 이 상황을 모른채 해당 함수를 썼다가 큰 예산 오류를 내버리게 된다.

이와 같은 상황은 서로 다른 액터가 의존하는 코드를 너무 가까이 배치했기 때문에 발생한다. SRP는 서로 다른 액터가 의존하는 코드를 서로 분리하라고 말한다.

## 징후 2: 병합

한 코드를 동시에 수정하게 되면, 병합 문제가 생기게 된다. 현대의 어떤 도구도 병합이 발생하는 모든 경우를 해결할 순 없기에, 항상 위험이 뒤따르게 된다.

## 해결책

[##_Image|kage@cxbdAz/btsqMhIkl23/VeXL1QhoSbc8IJaSEHk0C0/img.png|CDM|1.3|{"originWidth":695,"originHeight":320,"style":"alignCenter"}_##]

메서드가 없는 데이터 구조를 만들고, 각 클래스가 해당 데이터를 공유하도록 한다.

[##_Image|kage@cvtPRb/btsqJD0dzKj/AW6p2SWyvdcFYHqXjH9QK0/img.png|CDM|1.3|{"originWidth":688,"originHeight":234,"style":"alignCenter"}_##]

세 가지 클래스를 인스턴스화하고 추적해야 하는 문제는 퍼사드패턴으로 해결한다.

세 클래스의 객체를 생성하고, 요청된 메서드를 가지는 객체로 위임한다. (인터페이스 제공)

## 결론

SRP는 상위 수준에서도 활용이 가능하다.

컴포넌트 수준에서는 공통 폐쇄 원칙, 아키텍쳐 수준에서는 아키텍쳐 경계의 생성을 책임지는 변경의 축이 된다.
