# 9장

## LSP: 리스코프 치환 원칙

S 타입의 객체 o1 각각에 대응하는 T 타입 객체 o2가 있고, T 타입을 이용해서 정의한 모든 프로그램 P에서 o2의 자리에 o1을 치환하더라도 P의 행위가 변하지 않는다면, S는 T의 하위 타입이다.

[##_Image|kage@yqPQ5/btsqLkMmWo7/FMRqQ9vEDxKJNPK2pp45Lk/img.png|CDM|1.3|{"originWidth":691,"originHeight":339,"style":"alignCenter"}_##]

License 하위 타입 중 무엇을 사용하는지에 전혀 의존하지 않기 때문에 , LSP 준수.

## LSP와 아키텍쳐

잘 정의된 인터페이스와 , 해당 인터페이스의 구현체끼리의 상호 치환 가능성이 곧 LSP.

LSP를 어겼을 때 아키텍쳐에서는 어떤 일이 발생할까?

택시 파견 서비스

시스템이 고객에게 알맞은 기사를 선택하고 , 해당 기사의 URI를 이용해 파견하는 서비스가 존재한다고 가정하자.

```
purplecab.com/driver/Bob
```

put 방식의 호출

```
purplecab.com/driver/Bob
	/pickupAddress/jayanglo
	/pickupTime/153
	/destination/ord

```

이때, 서로 다른 택시업체들이 destination필드를 다른 방식으로 처리한다면 , (ex dest)

해당 업체들을 모듈 내에서 모두 조건문으로 다르게 처리해주어야 할 것이다.

효율도 떨어지고, 오류도 많이 발생하는 일이 될 것

여기서 택시업체들은, 한 인터페이스의 구현체들이라고 보면 된다.

### 결론

LSP는 아키텍처 수준까지 확장할 수 있고, 반드시 확장해야만 한다. 치환 가능성을 조금이라도 위배하면 시스템 아키텍처가 오염되어 상당량의 별도 메커니즘을 추가해야 할 수도 있기 때문이다.
