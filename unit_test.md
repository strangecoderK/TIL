## Unit Test

특정 언어와 상관 없이 개발의 품질을 높이기 위한 하나의 공정이다.

### 테스트 방법

1. 수동테스트 : 인간이 하는 테스트
2. 단위 테스트 : 1개의 함수를 테스트
3. 통합 테스트 : 여러개 연관된 클래스나 함수를 함께 테스트

### 테스트 방법론

1. 화이트박스 테스트

- 내부 구조와 동작에 중점을 두고 테스트한다.

- 코드의 내부 로직, 제어흐름, 데이터 흐름 등을 이해하고 검증하는데 사용한다.

- 테스트 케이스를 설계할 때 코드의 특정 부분을 직접 확인한다.

  ex) 주요기법: 구문 검사, 경로 검사, 조건/분기 검사

2. 블랙박스 테스트

- 내부정보 알필요 없고, 사용자 관점에서 테스트한다.

- 여기서 사용자란 클래스의 메서드를 사용하는 다른 개발자를 칭한다.

- 테스트 케이스는 입력 값과 예상 출력 값에 기반하여 설계한다.

- 요구 사항을 충족하는지 확인하고, 시스템의 기능적 및 비기능적 요구 사항을 테스트한다.

  ex) 주요기법: 등가 분할, 경계 값 분석, 상태 전이 테스트

### Unit test

* 새로운 기능을 추가하거나 기존 기능을 변경했을 때, 앱이 여전히 제대로 동작한다는 것을 보장하기 위해 테스트코드를 만들 수 있다.
* 특정 모듈이 의도한대로 잘 작동하는가를 테스트하는 가장 작은 단위의 테스트
* 모듈 = 메서드, 기능

### 테스트의 장점

* 장애에 관한 신속한 피드백
* 개발 주기에서 조기 장애 감지
* 회귀에 신경 쓸 필요 없이 코드를 최적화 할 수 있도록 하는 더 안전한 코드 리팩토링

### Unit test 가 필요한 경우

- DB
    - 스키마가 변경되는 경우
    - 모델 클래스가 변경되는 경우

- Network
    - 예측한 데이터가 제대로 들어오는지 (Dto → mapper → model)

- 데이터 검증
    - 예측한 데이터를 제대로 처리하고 있는지

### 테스트 코드 작성

1) 테스트코드는 테스트 디렉토리 안에 원본 파일명 뒤에_test를 붙여 파일명을 만들고 그곳에 작성한다.

2) given(준비) → when(실행) → then(검증) 기법을 사용한다.

3) 테스트 코드 실행 → 결과 확인→ 함수 수정

* 가능한 모든 가능성의 범위를 테스트 하는 것이 좋은 테스트 케이스 : 동등분할, 경계값 분석 등의 기법

테스트 중심으로 개발하는 방법론을 TDD (Test Driven Development) 라고 한다 : 모든클래스를 테스트코드를 짜고 여기에 맞춰 클래스를 짬

### Test Double

* 테스트를 진행하기 어려운 경우에 테스트가 가증하도록 만들어주는 객체.

* dummy, stub, spy, mock, fake 여러개가 있지만 모호한 경계를 가지므로 용어에 집착할 필요는 없다.

### mock 객체 활용

네트워크 통신 테스트를 위해 매번 실제로 통신을 한다면 비용, 시간, 불확실성 (서버 에러 등) 이 증가하기 때문에 네트워크 환경에 의존하지 않고 가짜 객체로 대체한다.

네트워크 연결이 안되거나 서버가 아직 완성되지 않았을때, → 데이트 받을 상황이 아닐때 → 가짜데이터를 받아서 → 테스트 할 수 있다.

* 다형성을 활용하면 테스트 할 때 원하는 객체를 활용 가능하다.
* 의존하는 클래스를 interface로 변경하여 사용한다.
* 의존하는 클래스가 mock 데이터를 주게 한다.
* dart의 느슨한 규칙을 응요한 변칙방법을 활용하여 mock 클래스를 구현한다. 