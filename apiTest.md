# API test
- 개발한 API를 test 하고, 결과를 공유하여 API 개발의 생산성을 높여주는 기능입니다.
- postman, insomnia 와 같은 상용 솔루션과 비슷한 기능을 제공하지만 aTworks의 추가 기능도 존재합니다. 
- Login API 연계된 session 관리, 이전 test 이력 조회, 듀얼 test 결과 비교 기능


- Sample 화면
![image](https://user-images.githubusercontent.com/85854794/221113410-a3c9b1e2-896c-4844-9cb0-4d7e2433446b.png)


### Login API 연계된 session 관리
- 각 Server에 맞는 Login 방식과 정보를 미리 저장한 상태에서 server를 변경하면 test 수행
- auth2, sso 등의 login 형태도 지원함
- 사용자는 Login 세션은 신경쓰지 않고 테스트 수행 


### 이전 test 이력 조회
- log 수집, aTworks를 활용하여 test 수행한 request 데이터를 조회할 수 있습니다.
- test 결과를 db에 저장하여 각종 통계로 산출할 수 있습니다.


### test 결과 비교 기능
- 한 화면에서 2개의 API test를 수행하고 그 결과의 일치여부를 확인해볼 수 있습니다. 
- 동일한 API를 서로 다른 server로 test 하거나 동일한 server에 body 데이터를 변경하면서 test 수행
- [데이터 직렬화](https://github.com/atworks-sk/atworks_tutorials/blob/main/business/dataSerialization.md) 를 통해 구조가 변경된 API도 비교가 가능합니다.

![image](https://user-images.githubusercontent.com/85854794/221119837-d8ead327-0f37-4558-a05d-89db9c1bde6a.png)
 
 
