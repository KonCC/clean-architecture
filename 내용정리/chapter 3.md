# 3장 패러다임 개요
## 구조적 프로그래밍(Structed Programming)
> 구조적 프로그래밍은 제어흐름의 직접적인 전환에 대해 규칙을 부과한다.

최초로 적용된 패러다임이다.
데이크스트라는 무분별한 점프(`goto`)는 프로그램 구조에 해롭다는 사실을 제시했다.
이러한 점프문들을 if/then/else와 do/while/until과 같은 구조로 대체했다.

## 객체 지향 프로그래밍(Object-oriented Programming)
> 객체 지향 프로그래밍은 제어흐름의 간접적인 전환에 대해 규칙을 부과한다.

알골(ALGOL) 언어의 함수 호출 stack frame을 heap으로 옮기면, 함수 호출이 반환된 이후에도 함수에서 선언된 지역 변수가 오랫동안 유지될 수 있음을 발견했다.
이런 함수가 클래스의 생성자가 되었고, 지역 변수는 인스턴스 변수, 중첩 함수는 메서드가 되었다.

함수 포인터를 특정 규칙에 따라 사용하는 과정을 통해 필연적으로 다형성이 등장했다.

## 함수형 프로그래밍(Functional Programming)
> 함수형 프로그래밍은 할당문에 대해 규칙을 부과한다.

알론조 처치(Alonzo Church)가 발명한 람다(lambda) 계산법이 LISP 언어의 근간이 되었다.
람다 계산법의 기초가 되는 개념은 불변성(immutability)으로, 심볼의 값이 변경되지 않는다는 개념이다.

## 생각할 거리
각 패러다임은 무엇을 해야 할지를 말하기보다, **무엇을 해서는 안 되는지**를 말해준다.
  - 구조적 프로그래밍 : goto문
  - 객체 지향 프로그래밍 : 함수 포인터
  - 함수형 프로그래밍 : 할당문
프로그래밍 패러다임은 앞으로도 위의 세 가지밖에 없을 것이다.