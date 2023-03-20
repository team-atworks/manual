# aTworks architecture
- aTworks는 web 기반의 관리자 화면, aTworks server, api 호출 이력을 조회하는 clinet 프로그램으로 구성되어 있습니다.
  
![image](https://user-images.githubusercontent.com/85854794/221502743-9b2e9705-6ba5-4113-87b7-bfc36c5539de.png)

### web 기반의 관리자 화면
- 개발자, 테스터가 URL로 접속하여 테스트를 수행하는 web 기반의 관리자 페이지입니다. 
- 서버관리, API 구조, bulk test, scenario test 등을 처리할 수 있습니다. 
- aTworks server 와 http 통신, aTworks client 와는 websocket으로 통신하여 사용자에게 정보를 전달해줍니다.
- 사용 기술 : reactJs, Bootstrap, websocket

### aTworks server
- spring 기반의 was application으로 관리자 화면과 RESTful api 방식으로 통신합니다. 
- log collect, source analysis, api test 등의 기능을 가지고 있습니다. 
- spring batch를 활용한 bulk test 기능도 지원합니다. 
- 사용 기술 : spring boot, jpa, OAuth 2.0, spring batch

### aTworks client 
- selenium 을 활용한 api 호출이력을 조회하는 window/mac client 프로그램으로 별도의 설치파일을 제공합니다. 
- 사용 기술 : python, selenium, install shield 

### aTworks 제원

![image](https://user-images.githubusercontent.com/85854794/221505187-2c78f591-b61a-4293-9269-dd627a593817.png)
