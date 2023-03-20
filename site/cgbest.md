# C공제 전환 프로젝트 
### 프로젝트 개요
- ui, framework 전환 프로젝트 (data 구조가 xml에서 json으로 변경)
- framework 자동 전환 소스에 대한 검증은 aTworks로 수행

### xml, json 전환
- asis 에서는 xml 특이사항 존재 (data가 모두 String type, List 구조가 특수한 key로 구분)
- 프로젝트 수행팀에서 xml에서 json으로 변경하는 role을 정리하지 않아서 business 개발자들에 따라서 임의로 처리함
- xml 최상위 root node에 attribute는 header 데이터로 사용하고 있었는데 tobe에서 버려짐 (json->xml 변경은 불가)


### test 방법

![image](https://user-images.githubusercontent.com/85854794/221454115-0da24d30-409a-44bc-9e83-472ffb2a376f.png)


### test report
- 6월 26,29일 2일치 log에서 분석된 test case 중 Long transaction 일부를 제외한 전건 수행 (총 385,168건 * 2)
- API 종류는 1712건 (CRUD)
- database는 실제 운영서버 기준 26일로 rollback 한 상태
- asis(xml), tobe(json) 동시 test 후에 결과를 비교하는 방식을 사용
- test 소요시간 7시간 (tobe db에 sequence 문제로 인해 속도 지연현상 발생)

- server test 결과

| server| total count| success count| fail count| success rate|no response| reponse time|
|---|---|---|---|---|---|---|
| asis(xml)| 385,168| 362,076|23,092| 94%| 29|0.29s|
| tobe(json)| 385,168| 352,463|32,705| 91.5%| 688|0.16s|


### 개발자에게 결과 확인 요청한 내용
- 특정조건에서 Long transaction으로 판단되는 API  
- system error code가 상이한 API 
- 정상적으로 개발되지 않은 API
- 특정 필드값이 상이한 API
- asis, tobe 사이의 order by가 다른 API 


### 2차 집중 test
- 대상은 고객사에 정의한 중요한 금액, 안내내용, 전표처리 등에 관련된 API 12개
- 6월 마지막주 (5영업일) 전체 log 대상으로 전건 테스트 수행 
- 결과 : 금액 전부일치, 안내내용 차이(띄어쓰기 부분만 검출됨), 전표처리 결과 일치
