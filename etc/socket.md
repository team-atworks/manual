# Socket test 수행방안

- aTworks는 HTTP 통신의 API 테스트만 지원하고 있는데 일부 금융사업(증권)에서는 속도와 정확성 문제로 인해 TCP 통신을 이용한 시스템으로 구축되어 있기 때문에 보안할 필요가 있습니다.


### 현재 기능 및 필요성 
- 현재 aTworks는 Http 통신방식의 API만 테스트만 지원
- 일부 금융사업 Project에서는 속도/정확성 문제로 인해 TCP 통신으로 구축되어 있습니다.
- 증권팀에서 수행예정인 대체거래소 프로젝트의 경우 aTworks가 제안에 포함되었습니다.


### 개발 방법
- HTTP는 기본적으로 TCP 기반으로 만들어진 Protocol 이기 떄문에 크게 다르지 않습니다. 
- 실제 개발로 들어가면 네트워크 계층이 달라지게 되어 직접 구현해야 되는 부분이 많은데 Netty Framework를 사용하여 Handshake, Connection Health check, Common Header 기능을 개발할 예정입니다.


### Go 언어를 활용한 테스트 Socket 서버
- Go 언어는 GoRoutine(이하 고루틴)이라는 비동기 메커니즘을 제공하는데 이를 통해 복잡한 분산처리를 빠르게 처리할 수 있습니다.
- [TCP/IP 테스트 서버 소스 코드](https://github.com/atworks-sk/go_socket_server.git)
![image](https://user-images.githubusercontent.com/85854794/223013416-5acf7bcd-578c-4a18-8a81-9b0771e8b1d0.png)


### TCP/IP 테스트 서버 구축

![image](https://user-images.githubusercontent.com/85854794/223013613-911c4bae-37c2-4daa-9e5b-a51074ba8bf4.png)


### aTworks Socket 통신 (실시간)  
- Socket 통신은 http 통신과 달리 매번 신규로 커넥션을 연결하게 되면 대상서버에 부하가 발생하게 됩니다. 
- N개의 커넥션을 연결해 두고 이를 요청한 순서대로 호출하는 방법으로 진행합니다.

![image](https://user-images.githubusercontent.com/85854794/223013726-23c65245-f8eb-4f63-a857-f83e9f9c0b9e.png)


### aTworks Socket 통신 (배치) 
- 배치 프로세스는 http와 거의 동일하게 수행됩니다. 차이점은 http는 배치 그룹이 수행될 때마다 초기화 작업을 진행 후에 수행되지만 Socket의 경우 배치가 최초 수행될때만 초기화 작업이 수행됩니다.

![image](https://user-images.githubusercontent.com/85854794/223013784-a8acc713-5e18-4ece-b4c2-7e58b838f3c2.png)
