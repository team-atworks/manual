# scenario test
- sceanrio test 는 API 호출, SQL 조회등의 transaction 단위를 연결하여 순차적으로 테스트를 수행할 수 있습니다.
- scenario -> case -> step 단위로 구성되며, 상위단계는 N개의 하위 단계를 가질 수 있습니다. 
- API 호출, SQL 조회등은 각각 1개의 step으로 구성됩니다. 

![image](https://user-images.githubusercontent.com/85854794/221357342-23929064-9d47-4699-82e6-168e186e3fc3.png)


### step 구성 방법

- login api 등록
  - 인증이 필요한 server에서 등록하지 않은 상태에서 테스트를 수행하는 경우 401 인증애러가 발생합니다. 
  - server 별로 등록된 default id/password을 사용하거나, 직접 입력해서 수행할 수 있습니다.

- 등록된 API 조회

- 개발자 도구 활용
  - Browser(Chrome, Edge)의 개발자도구를 활용하여 쉽게 전문을 등록할 수 있습니다. 
  - 개발자도구 -> Network 탭 -> 우측 마우스 -> Copy -> Copy as fetch
  
    ![image](https://user-images.githubusercontent.com/85854794/221357942-9f4fdfc4-a0d5-4420-a2ce-1200e767791f.png)

- SQL 등록 
  - 등록된 database로 select query를 수행하여 결과를 scneario test 에서 활용할 수 있습니다. 
  - delete, update, create, drop 명령어 사용금지

- script 등록 
  - 각각 step 들을 연결해주는 기능을 하는 시각화된 script 기능을 제공합니다. 
  - timeout, copy value, compare value 기능이 있습니다. 


### script 상세 설명 

- timeout
  - step 사이에 일정한 term을 두고 싶을때 사용합니다.

- copy value
  - text, 난수, 변수, 상위 step의 response data 값을 copy 하여 변수 또는 하위 step의 request data 값으로 이동합니다. 
  - script에서 사용되는 값 유형

|유형| 설명| step| text| number| 난수| 변수|
|---|---|---|---|---|---|---|
|copy from| copy 를 수행할 item| O| O| O| O| O|
|copy to| copy 가 수행될 item| O| X| X| X| O|
|compare item| compare 가능한 item| O| O| O| X| O|

- compare value
  -  text, 변수, step의 response data 값을 비교하여 후속 프로세스를 정하게 됩니다. 
  -  비교 문법 : ==, !=, <, <=, is null 
  -  후속 프로세스 : scenario 성공, 실패 처리(후속 step 수행되지 않습니다.), 특정 후속 step 으로 이동



### scenario test 예시
- 가상의 scenario test 구성하였습니다. 

![image](https://user-images.githubusercontent.com/85854794/221363459-209c3e8a-558a-4f3d-babe-6108689c2d5c.png)
```
1. 난수로 고객 이름과 주민등록번호를 생성
2. [1]에서 전달받은 고객 이름과 주민등록번호로 신규 고객 등록 API 호출 (신규 고객 생성)
3. [2]에서 생성된 고객 ID로 계약 체결 API 호출 (신규 계약 생성)
4. [3]에서 생성된 계약 ID로 업무 DB를 조회하여 데이터 확인
5. 계약번호로 조회된 데이터 존재 유무 확인
- 5-1. scenario test 종료 (실패)
- 5-2. [3]에서 생성된 계약 ID로 계약해지 API을 호출하여 계약 해지
6. 해지 API의 결과를 확인
- 6-1. scenario test 종료 (실패)
- 6-2. scenario test 종료 (성공)
```



