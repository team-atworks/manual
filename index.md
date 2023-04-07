# atworks 테스트 자동화 도구 소개
### aTworks 이해하기
> aTworks는 Application Programming Interface (API) 테스트를 효율적이고 정확하게 할 수 있게 도와주는 도구 입니다.  
> 화면을 대체하여 API를 테스트하는 도구이며, 화면을 테스트는 하는 도구는 아닙니다.
<img src = "https://user-images.githubusercontent.com/52950400/230523544-35b62e57-8184-4872-9b64-84acfceeeacc.png" width="70%" height="30%">

- [수동 test 문제점](https://github.com/team-atworks/manual/blob/main/etc/manualTest.md) 
- [aTworks 시스템 구성](https://github.com/team-atworks/manual/blob/main/business/architecture.md)


### 상용 솔루션과 차이점
> 상용 API 테스트 상용 솔루션이지만 aTworks 만의 특별한 기능도 가지고 있습니다.
<img src = "https://user-images.githubusercontent.com/52950400/230524776-4e53e7ee-e67a-4e00-9e20-71394f77703c.png" width="70%" height="30%">

- Source 분석, Log 수집 도구를 통한 API구조, Log 기반에 테스트 케이스를 자동 생성합니다. 
- 화면에서 발생한 API 호출 이력을 녹화하여 테스트 케이스로 등록하는 방법을 제공합니다. (IE 기능 제한)
- bulk, scenario, schedule test 등의 concept을 가진 테스트 기능을 지원합니다. 
- web으로 구성된 시각화된 GUI 제공하여 업무 화면에 들어가지 않아도 테스트를 수행할 수 있습니다. 
- 2개의 서버에 동시 테스트를 수행하고 상세한 결과를 비교해볼 수 있습니다.


### 주요기능 

- [시스템 분석](https://github.com/team-atworks/manual/blob/main/systemAnalyze.md)
적용하는 시스템 여건에 맞게 Source 분석, Log 수집을 통해 test 을 위한 기반데이터를 생성합니다.
- [API test](https://github.com/team-atworks/manual/blob/main/apiTest.md) : 단순한 API test 기능이지만 API 구조, Test case 등이 자동으로 생성되어 있고, 로그인 멀티서버 테스트 기능도 추가로 제공합니다.
-  [bulk test](https://github.com/team-atworks/manual/blob/main/bulkTest.md) : 이전에 test된 내용을 변경없이 multi thread 로 대량건의 test case를 원하는 시간에 수행하는 기능입니다.
-  [API 호출 이력 녹화](https://github.com/team-atworks/manual/blob/main/apiRecord.md) : 화면에서 발생한 API 호출 이력을 녹화하여 test case로 등록하는 방법을 제공합니다
-  [scenario test](https://github.com/team-atworks/manual/blob/main/scenarioTest.md) : API 호출, SQL 조회등의 Transaction 단위를 연결하여 순차적으로 테스트를 수행할 수 있습니다.
 
 
### 적용 사례

- [C공제 차세대 프로젝트](https://github.com/team-atworks/manual/blob/main/site/cgbest.md)
- [K손해보험 프로젝트 (준비중)]


### 적용 방안
- [기존 프로젝트 운영 적용](https://github.com/team-atworks/manual/blob/main/project/systemMaintenance.md)
- [신규 프로젝트 적용](https://github.com/team-atworks/manual/blob/main/project/systemIntegration.md)
- [전환/EOS 프로젝트 적용](https://github.com/team-atworks/manual/blob/main/site/eos.md)


