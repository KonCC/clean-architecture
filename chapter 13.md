# 13장 - 컴포넌트 응집도

- 어떤 클래스를 어떤 컴포넌트에 포함시켜야 할까?
- 컴포넌트 응집도와 관련된 세가지 원칙

# REP: 재사용/릴리스 등가 원칙 (Reuse/Release Equivalence Principle)

> 재사용 단위는 릴리스 단위와 같다
> 
- 모듈 관리 도구를 통해 소프트웨어 재사용이 가능해짐
- 릴리스 절차를 통해 추적 관리가 되지 않거나 릴리스 번호가 부여되지 않는다면 컴포넌트는 재사용할 수 없다.
    - 릴리즈 번호가 없다면 재사용 컴포넌트들이 서로 호환되는지 보증할 방법이 없음
    - 개발자들은 릴리즈 단위로 새로운 버전을 쓸지 기존 것을 계속 사용할 지 결정
- 아키텍쳐 관점
    - 단일 컴포넌트는 응집성 높은 클래스와 모듈들로 구성되어야 함
        - 컴포넌트를 구성하는 모든 모듈은 서로 공유하는 중요한 테마나 목적이 있어야 한다.
        - 하나의 컴포넌트로 묶인 클래스와 모듈은 함께 릴리스 할 수 있어야
            - 버전 번호가 같아야 하고 동일한 릴리스로 추적관리되어야 한다.
                - 재사용을 할 수 있다.

# CCP: 공통 폐쇄 원칙 (Common Closure Principle)

> 동일한 이유로 동일한 시점에 변경되는 클래스를 같은 컴포넌트로 묶어라. 서로 다른 시점에 다른 이유로 변경되는 클래스는 다른 컴포넌트로 분리하라
> 
- SRP를 컴포넌트 관점으로 작성한 것
- 단일 컴포넌트도 변경 이유가 여러개 있어서는 안된다.
- 유지보수성이 재사용성보다 훨씬 중요
    - 코드가 변경되어야 할 때 여러 컴포넌트에서 변경이 발생하는 것보다는 한 컴포넌트에서 다 발생하는 편이 낫다 → 그 컴포넌트만 재배포하면 되니까
- OCP의 Closure와 뜻이 같다.
    - 발생할 가능성이 있거나 과거에 발생했던 공통적인 변경에 대해 클래스가 닫혀있도록
    - 변경에 영향을 주는 컴포넌트가 최소한으로 한정되도록

# CRP: 공통 재사용 원칙 (Common Reuse Principle)

> 컴포넌트 사용자들은 필요하지 않는 것에 의존하게 강요하지 말라
> 
- 같이 재사용되는 경향이 있는 클래스와 모듈들은 같은 컴포넌트에 포함해야 한다.
- ex. container 클래스와 해당 클래스의 이터레이터(iterator) 클래스
- 동일한 컴포넌트로 사용하면 안되는 클래스가 무엇인지도 말해준다.
    - 사용하는(using) 컴포넌트가 사용되는 (used) 컴포넌트의 단 하나의 클래스만 사용하더라도 의존성이 생겨서 사용되는 컴포넌트가 변경될 때마다 사용하는 컴포넌트도 같이 변경해야 할 가능성이 높다.
    - ISP의 포괄적인 버전
        - ISP - 사용하지 않는 메서드가 있는 클래스에 의존하지 말라
        - CRP - 사용하지 않는 클래스를 가진 컴포넌트에 의존하지 말라

# 컴포넌트 응집도에 대한 균형 다이어그램

- REP와 CCP는 컴포넌트를 크게 만든다
- CRP는 컴포넌트를 작게 만든다.
- REP, CRP에 중점 - 사소 변경이 발생했을 때 많은 컴포넌트에 영향을 미침
- REP, CCP에 중점 - 불필요한 릴리스가 빈번
    - 개발팀이 관심을 기울이는 부분을 충족시키게 균형을 맞춰야
    - 초기에는 CCP가 중요하지만 시간이 지날수록 REP가 중요해짐

# 결론

- 클래스를 묶어서 컴포넌트를 만들 때 재사용성가 개발 가능성 사이에서 어플리케이션 요구사항에 맞게 균형을 잡는 일이 중요
- 이 균형은 프로젝트의 진행사항에 따라 유동적으로 변경가능