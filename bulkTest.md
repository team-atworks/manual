# bulk test
- log 분석, aTworks test 통해 수집된 test case를 대량으로 test 하는 기능.
- multi thread로 수행하여 시간을 단축합니다. 
- 최대 2개의 server에 동시에 test 하고 결과를 비교할 수 있습니다.
- 사용중인 AP server에 부하가 없는 시간에 스케줄링하여 test 수행합니다.


![image](https://user-images.githubusercontent.com/85854794/221136037-7fe85406-8977-429b-9e02-87f5ab2d9138.png)


### bulk test 한계
1. aTworks에서 아무리 병렬로 수행하여도, 운영 서버에 발생한 수백만건의 Transaction을 단시간에 처리할 수 없습니다. (AP서버 부하발생)
2. 조회를 제외한 cud의 경우 순서대로 보낸다고 처리되지 않습니다. (AP서버의 pk 생성규칙)
3. 데이터(DB)를 동일하게 구성한 뒤에 보내면 되지 않나요? 일반적인 시스템은 그렇게 잘 만들어져 있지 않습니다. 
4. 대량의 test case를 보내서 대략의 결과 리포트를 추출하는 기능입니다. 정말 모든 테스트를 자동으로 해주는 기능은 아닙니다. 

### bulk test에서 의미있는 데이터 
1. 일반적인 시스템의 80% 이상은 조회성 API 입니다. 
2. asis/tobe 시스템에 동일한 request 발송하게 되면 동일한 error 가 발생 해야 됩니다. 

