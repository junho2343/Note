# Unit Test(단위 테스트)

    - 독립적인 함수 모듈 클래스를 테스트 (자동차로 비유를 하자면, 바퀴에 대한 테스트)

#### Test Runner

- 테스트 실행 후 결과 생성
- **Mocah** 라는 라이브러리가 대표적으로 사용됨

#### Assertion

- 테스트에 대한 조건, 비교를 통한 로직
- **Chai** 라는 라이브러리가 대표적으로 사용됨

## 🃟 Jest

- Test Runner, Assertion 모두 수행하는 자바스크립트 테스팅 라이브러리

> [Jest 공식 문서](https://jestjs.io/)

### Jest 장점

- **zero config**, 별 다른 설정 없이 사용 가능!
- **snapshots**, 브라우저 UI 환경에서 테스트 할 때 사용, 큰 오브젝트 현재의 상태 찰칵
- **isolated**, 테스트가 각각의 프로세스에서 진행되기 때문에 성능, 속도가 좋다.
- **great api**, 사용하기 쉬운 라이브러리가 내장되어 있다.

### Jest 환경 설정

```shell

"test": "jest --(watch|watchAll)"

```

- **watchAll** : 코드가 변경 될 때 마다, 모든 테스트를 재실행한다.
- **watch** : 이미 git에 커밋된 파일 X, 수정 중인 파일만 테스트를 재실행한다.

> [cli options](https://jestjs.io/docs/cli)

### Jest Matchers

- **toBe** : 두 값이 동일한지 확인하고 싶을 때 사용한다.
- **toEqual** : 객체 또는 배열의 모든 필드를 재귀적으로 확인하기 때문에 객체의 값이 동일한지 확인하고 싶을 때 사용한다.

### 비동기 함수 테스트

1.  it 메소드에 콜백 함수를 전달할 때, done 인자를 전달하여 수동으로 테스트가 끝났다는 것을 명시하는 방식 (비추 👎)

- done() 이 호출되기 전까지 테스트가 끝나지 않는다. return, await 방식보다 느리다.

2.  it 메소드의 콜백 함수에 메소드 자체를 return 해주는 방식

3.  it 메소드의 콜백 함수에 async 키워드를 붙이고 비동기 코드 앞에 await 키워드를 붙여주는 방식

> [Jest - asynchronous](https://jestjs.io/docs/asynchronous)

### Mock (Mockist)

- 가짜를 진짜인 듯하게 흉내내서 **기능이 잘 동작하는지 확인**하는데 사용되는 객체이다.
  - 실제 내부 구현체가 실행되지 않는다.
- 모듈 간 의존성 있는 부분을 대신하여(=Mock) 모듈 간의 의존성을 분리한다.
- Mock은 테스트가 올바르게 **호출되었는지(행동)를 검증**한다.

> Mock 남용 🙅‍♀️
>
> - 코드의 아키텍쳐를 개선하지 않고 Mock을 사용해 코드 개선을 피하려고 하면 안된다!

### Stub (Classic)

- 가짜를 진짜인 듯하게 흉내 내는 점은 Mock과 비슷하다. Stub은 실제와 동일하게 동작하는 가짜 객체를 만들어서 실제로 동작하도록 한다.
- 테스트에서 호출된 요청에 대해 미리 정해둔 값을 리턴한다.
- Stub은 테스트의 최종 결과 **값(상태)을 검증**한다.

> - [What's the different mock & stub](https://martinfowler.com/articles/mocksArentStubs.html)
> - [typescript로 배우는 stub, mock, spy의 차이점](https://charming-kyu.tistory.com/41?category=1040183)
