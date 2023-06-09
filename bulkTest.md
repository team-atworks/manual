# bulk test 
> 로그 분석 및 aTworks 테스트를 통해 수집된 테스트 케이스로 대량건을 테스트 하는 기능 입니다. 

### 주요특징
- Multi Thread 프로세스 기반으로 수행하여 대량 테스트 수행시간을 단축 합니다.
- API 서버가 부하가 없는 시간(새벽 등)에 스케줄링 기능을 활용하여 테스트를 수행합니다. 
- 최대 2개 서버에 동시에 테스트하고 결과를 비교할 수 있습니다.

![image](https://user-images.githubusercontent.com/85854794/221136037-7fe85406-8977-429b-9e02-87f5ab2d9138.png)

### bulk test 오해
> 간혹 bulk test의 기능을 오해하는 부분이 있어 설명 드립니다.
1. aTworks에서 병렬(Multi-Thread)로 수행하여도, 운영 서버에 발생한 수백만건의 Transaction을 단시간에 처리할 수 없습니다. (실제 작업은 AP가서버가 수행하므로 AP서버 부하발생)
2. 조회를 제외한 cud의 경우 순서대로 요청하여도 처리되지 않습니다. (AP서버의 pk 생성규칙 등)
3. 데이터(DB)를 동일하게 구성한 뒤에 보내면 되지 않나요? 일반적인 시스템은 그렇게 잘 만들어져 있지 않습니다. 
4. 모든 테스트를 자동으로 해주는 기능은 아닙니다. 
대량의 test case를 보내서 대략의 결과 리포트를 추출하는 기능입니다. 

### bulk 테스트로 얻는 의미있는 데이터 
1. 일반적인 시스템의 80% 이상은 조회성 API 입니다. 
2. asis/tobe 시스템에 동일한 request 발송하게 되면 동일한 error 가 발생 해야 됩니다. 

### bulk test 활용
- 대량 테스트결과를 통하여 다향한 통계 데이터를 산출하여 활용할수 있습니다.
  - Test Coverage 확인 (aTworks에 등록된 API중 테스트 성공율 확인)
  - 다양한 통계 데이터: API별 성공/실패율, 응답지연 API 등
- API 구조 변경 없이 서버 마이그레이션과 같은 프로젝트에 매우 적합합니다.