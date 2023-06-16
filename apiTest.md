# API test
> 개발한 API를 단건 및 반복 테스트를 수행하며 결과를 공유하여 **개발 생산성**을 높힐수 있습니다.
> 로그인 API와 연계된 사용자 세션관리, 테스트 이력조회, 테스트 재사용, 듀얼테스트 결과 비교등 상용솔루션(Postman,insomnia 등)이 가진 기능 외 **추가기능**도 제공 합니다.

### Login API와 연계된 session 관리
- 각 API Server에 맞는 Login 정보를 사전에 저장하여 Server 변경시에도 별도 로그인정보 없이 테스트를 수행합니다.
- 세션,쿠키,OAuth,SSO 등의 로그인 방식도 지원합니다.
- 사용자는 Login 세션은 신경쓰지 않고 테스트합니다.

### 이전 테스트 이력 조회 및 재수행
- aTworks를 활용하여 기존에 수행한 테스트 Request 데이터 및 Response 데이터를 조회할 수 있습니다.
- 기존에 수행한 테스트와 동일하게 테스트 할 수 있습니다.
- 테스트 결과를 데이터베이스에 저장하기 때문에 각종 통계데이터(API별 응답속도, 실패율 등 )를 산출할 수 있습니다.


### test 결과 비교 기능
- 동일한 API를 **다른 2개서버**에 테스트를 수행하고 응답데이터 일치여부를 확인해 볼 수 있습니다. 
- 동일한 API를 동일한 서버에 **요청 데이터 다르게**하여 테스트를 수행하고 응답데이터 일치여부를 확인해 볼 수 있습니다.
- API 응답구조가 다르더라도 변경된 규칙만 존재한다면 API 비교가 가능 합니다. [(타 프로젝트 사례)](./business/dataSerialization.md)

## 예시화면
- 단건테스트 수행화면
![image](https://user-images.githubusercontent.com/85854794/221113410-a3c9b1e2-896c-4844-9cb0-4d7e2433446b.png)

- 듀얼테스트 수행화면
![image](https://github.com/team-atworks/manual/assets/25805562/b570e161-5527-46a7-8275-b4dbcd563c62)

- 듀얼테스트 수행결과 비교화면
![image](https://github.com/team-atworks/manual/assets/25805562/2b5e4d19-0fcd-4170-8487-24838122c9db)
 
