## 17장 경계: 선 긋기

#### - 선은 한편의 요소가 반대편의 요소를 알지 못하도록 만든다
#### - 초기에 그어지는 선들은 가능한 오랫동안 결정을 연기시키기 위해 그어진다
#### - 그 결과로, 핵심적인 업무 로직을 오염시키지 못하게 만드는 목적으로 쓰인다
---
> 어떻게 선을 그을까?  
관련이 있는 것과 없는 것 사이에 선(경계)을 긋는다 – 비즈니스 규칙 | 데이터베이스 | GUI 

![img](../images/chapter%2017-1.png)  
- 업무 규칙과 DB 사이에 선을 그어서 DB에 대한 생각을 미룰 수 있게 되었다
- 업무 규칙에서 나오는 화살표가 없으므로 업무 규칙은 다양한 구현체를 교체할 수 있다
> 경계가 잘 그어지면 플러그인 구조를 띈다  
생성/확장/유지보수가 편하다

