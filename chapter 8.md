# 8장

## OCP : 개방 - 폐쇄 원칙

소프트웨어 개체는 확장할 수 있어야 하지만 ,변경 되어서는 안된다.

아키텍쳐 컴포넌트 수준에서 아주 중요한 의미를 가지게 된다.

## 사고 실험

재무제표를 웹 페이지로 보여주는 시스템이 있다고 해보자. 이해관계자가 동일한 정보를 보고서 형태로 변환해서 흑백 프린터로 출력해 달라고 요청했다고 해보자.

[##_Image|kage@Fnpfs/btsqJrls2tg/XL8x79KqksxY7cJBKwtWs0/img.png|CDM|1.3|{"originWidth":695,"originHeight":230,"style":"alignCenter"}_##]

SRP를 적용한 모습

보고서 생성은 두가지 책임으로 나뉘게 된다.

1.  보고서용 데이터를 계산하는 책임
2.  웹으로 보여주거나 종이로 프린트하기에 적합한 형태로 표현하는 책임

소스코드 의존성을 조직화하기 위해,

처리 과정을 클래스 단위로 분할하고, 이들 클래스를 아래와 같이 이중선으로 표시한 컴포넌트 단위로 구분해야 한다.

[##_Image|kage@cVPBKD/btsqRgB6JGv/L2sizoKP4KAq8nqLy7ter1/img.png|CDM|1.3|{"originWidth":695,"originHeight":591,"style":"alignCenter"}_##]

화살표가 열려 있다면 사용 using 관계이며, 닫혀 있다면 구현 implement 관계 또는 상속 inheritance 관계다. 여기서 주목할 점은 다음과 같다.

1.  모든 의존성이 **소스 코드** 의존성을 나타낸다.(화살표가 A클래스가 B클래스를 호출한다면 B 클래스는 A클래스를 호출할 수 없다)
2.  이중선은 화살표와 **오직 한 방향으로만** 교차한다. (모든 컴포넌트 관계는 단방향으로만 이루어진다는 뜻)

[##_Image|kage@zp7sR/btsqM7Z5h2F/kGd5hhBeO2HFZ8eoUf6pXk/img.png|CDM|1.3|{"originWidth":693,"originHeight":342,"style":"alignCenter"}_##]

가장 높은 수준의 정책을 포함하는 컴포넌트는 다른 어떠한 컴포넌트에게도 영향을 받지 않는다.

## 방향성 제어

위 클래스 설계에서 인터페이스들은 의존성을 역전시키기 위해 존재한다.

## 정보 은닉

추이 종속성이란 ? 클래스 A가 클래스B에 의존하고, 클래스 B가 클래스 C에 의존한다면 클래스 A는 클래스 C에 의존하는 것.

FinancialReportRequester 인터페이스는 FinancialReportController가 Interactor 내부에 대해 너무 많이 알지 못하도록 막기 위해서 존재한다.

즉 , Controller가 FinancialEntities에 대해 추이 종속성을 가지지 못하도록 존재.

## 결론

OCP의 목표는 시스템을 확장하기 쉽도록 하고, 변경으로 인해 시스템의 여러부분이 영향을 받지 않도록 하는 데 있따.

시스템을 컴포넌트 단위로 분리하고, 저수준 컴포넌트에서 발생한 변경으로 부터 고수준 컴포넌트를

보호하는 의존성 계층구조로 설계하자.
