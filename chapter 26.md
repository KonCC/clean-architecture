26장 메인 컴포넌트
궁극적인 세부사항

메인 컴포넌트는 가장 바깥 원에 해당하는가장 낮은 수준의 정책이다.

의존성 주입 프레임워크 (ex spring) 을 이용해 의존성을 주입하는 일을 메인 컴포넌트가 한다.

메인은 고수준의 시스템을 위한 모든것을 로드한 후 제어권을 고수준의 시스템에게 넘긴다.

→ 예시인 움퍼스 게임에서도 main 함수에서 게임의 메인 루프, 입력 명령어 해석을 처리하지만 명령어의 실제 처리는

다른 고수준 컴포넌트로 위임시킨다.

결론
메인은 애플리케이션의 플러그인이다.

메인은 플러그인이므로 설정별로 하나씩 두어 둘 이상의 메인 컴포넌트를 만들 수도 있다.

ex) 개발용 메인 플러그인, 별도의 테스트용 메인 플러그인 등등